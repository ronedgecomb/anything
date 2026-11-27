# Parallel work

Use parallelism only for independent work when the environment supports it and permission allows it. Sequential work is the default fallback when safe isolation or process management is unavailable.

## Ownership and inputs

- Give each contributor an explicit outcome, inputs, and ownership boundaries.
- Resolve shared decisions before independent implementation when that reduces rework. Do not split a tightly coupled task just to use more workers.
- Ensure each contributor can access the relevant material. A local absolute path works only in a shared filesystem; otherwise pass content or an accessible snapshot.
- Give the integration owner the responsibility for combining outputs and resolving conflicts.

## Isolation

Use the isolation the environment actually provides: separate drafts, artifact copies, native isolated workspaces, or Git worktrees when Git is present and appropriate.

- Avoid concurrent writers to the same artifact or mutable resource. Distinct files may still share a Git index, generated output, test state, or database.
- If the environment cannot support safe concurrent writes, sequence edits. Read-only investigation may still run independently.
- A Git worktree is an option, not a prerequisite. Follow the project's branch and integration strategy; do not require merge commits.
- New workspaces may lack dependencies or local configuration. Inspect their needs rather than assuming a main workspace's untracked or ignored files are present.
- Do not copy secrets, install dependencies, or change shared configuration merely to make a worker run. Use only inputs and setup actions authorized for the task.
- Clean up only task-owned workspaces and processes when permitted, preserving outputs and unrelated user state. Verify ownership and the exact target before destructive cleanup.

## Git worktrees

Reuse an isolated checkout supplied by the host when it fits the assignment. Create linked worktrees when workers need separate checkouts of the same Git repository. Each worktree has its own working files and index. Repository refs and most configuration are shared, so coordinate branch and configuration changes across workers. [Git worktree documentation](https://git-scm.com/docs/git-worktree)

### Choose the location

Follow the project's location convention. An ignored `.worktrees/` at the root of a stable coordinating checkout is a good default when the project's tools can handle nested checkouts. If the coordinator may itself be removed, place its workers in an allowed sibling location outside it. A sibling location also works when the tooling needs it or an ignored root is unavailable. Choose paths that stay accessible through integration.

For the default root, `/.worktrees/` in the root `.gitignore` shares the rule with the project when committed. The same pattern in the file returned by `git rev-parse --git-path info/exclude` applies to the local clone and its linked worktrees. Reuse existing rules and change them only when authorized. [Git ignore rules](https://git-scm.com/docs/gitignore)

For a root inside the coordinating checkout, verify that the directory has no tracked paths and that the ignore rule matches. These commands check the default location from the checkout's root.

```sh
git ls-files -- .worktrees/
git check-ignore -- .worktrees/
```

### Create and assign a worktree

Choose the intended base commit. Use the same commit for work items that need a common snapshot. Pick an unused path and a distinct branch for each independently editing worker, following project conventions. Check registered paths and checked-out branches with `git worktree list --porcelain`. For example, from the coordinating checkout with `HEAD` at the chosen base and the ignored root verified:

```sh
git worktree add -b work/report-filters .worktrees/report-filters HEAD
git -C .worktrees/report-filters status --short --branch
```

A new checkout starts from the selected commit. Supply permitted local inputs separately and check dependencies and configuration before running checks. If creation fails, inspect the worktree and branch state before retrying.

Give the worker its accessible path, starting commit, branch when present, and ownership boundaries. Have it confirm the checkout before editing and run project commands there. Record the path, starting commit, and any branch in the task record when one exists. Agree how results will return, such as local commits on the worker branch when allowed, or a patch or file set that includes any needed new files.

### Integrate and remove

After the worker and its processes finish, the coordinating agent collects and verifies the results. Preserve intended changes and verification artifacts outside the worker checkout, and verify the integrated result.

Match the exact resolved path to the task assignment and `git worktree list --porcelain`. Compare it with all resolved paths in the list to check for nested worktrees. Keep a parent checkout in place until its nested worktrees are safely removed or relocated. Check for tracked changes and untracked files, and inspect ignored directories that may contain results or another checkout. Ordinary removal can delete ignored files, including files in ignored nested checkouts. [Git removal implementation](https://github.com/git/git/blob/v2.55.0/builtin/worktree.c#L1240-L1335)

```sh
git -C .worktrees/report-filters status --short --untracked-files=all --ignored=matching
```

Once results are preserved and removal is authorized, remove the specific task-owned checkout from the coordinating workspace.

```sh
git worktree remove .worktrees/report-filters
```

Check the command result and verify that both the directory and its Git registration are gone. Git can unregister a worktree whose directory it could not fully remove. If removal reports an error, verify what remains before retrying and record the error and observed state in the task record or handoff. Keep Git's removal safeguards in effect and preserve the remaining files while resolving the failure. For authorized branch cleanup, verify that needed work is preserved under the project's integration rules before deleting the branch.

## Subprocess workers

Process creation does not by itself provide an agent. Confirm suitable worker tooling is already available and authorized.

Use a bounded task and an explicit working context. Track the process handle or session, output destination, expected completion, and failure state. Start workers only when you can collect their results and stop processes you own. Avoid shell-specific launch recipes in a portable brief.

Do not use subprocesses when delegation is prohibited, or treat a missing native feature as permission to change the environment's restrictions.

## Shared resources and integration

Assign ownership or separate instances for ports, services, databases, generated files, and test resources. Run checks sequentially when they would conflict.

Review and verify a stable artifact or known snapshot. If work changes during review, identify the changes and check the affected result again. Do not infer that read-only reviewers make simultaneous mutation or test runs safe.

Combine results using the available artifact or version-control mechanism. Resolve conflicting assumptions before claiming completion. A known temporary failure must be bounded and explained, then checked on the integrated result.
