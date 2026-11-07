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

## Subprocess workers

Process creation does not by itself provide an agent. Confirm suitable worker tooling is already available and authorized.

Use a bounded task and an explicit working context. Track the process handle or session, output destination, expected completion, and failure state. Start workers only when you can collect their results and stop processes you own. Avoid shell-specific launch recipes in a portable brief.

Do not use subprocesses when delegation is prohibited, or treat a missing native feature as permission to change the environment's restrictions.

## Shared resources and integration

Assign ownership or separate instances for ports, services, databases, generated files, and test resources. Run checks sequentially when they would conflict.

Review and verify a stable artifact or known snapshot. If work changes during review, identify the changes and check the affected result again. Do not infer that read-only reviewers make simultaneous mutation or test runs safe.

Combine results using the available artifact or version-control mechanism. Resolve conflicting assumptions before claiming completion. A known temporary failure must be bounded and explained, then checked on the integrated result.
