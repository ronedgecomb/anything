---
name: handoff
license: Apache-2.0
description: Prepare a copyable review or implementation brief for the user to pass to another agent. Use only when the user explicitly requests a handoff. Review mode captures the exact target and evidence. Implement mode captures the starting point, scope, and acceptance criteria.
disable-model-invocation: true
---

# Handoff

Start only when the user explicitly asks you to prepare a handoff. Keep preparation to reading the relevant context and drafting the brief. Return it to the user for manual transfer.

## Choose the mode

Use `review` for evaluation and `implement` for starting or resuming work. Follow the user's requested mode or the intent of their request. Ask which mode they want if the purpose is unclear.

## Gather the context

- Use the user's notes, relevant project instructions, artifacts, and any existing task record. Capture the goal, applicable constraints, decisions, and material open questions concisely.
- Identify the repository or project and the specific checkout or artifact. When Git is available, record the worktree path, branch or detached state, and commit. Specify which staged, unstaged, or untracked changes the recipient needs. For a diff review, identify the exact comparison base and target.
- For in-scope local changes in a shared checkout, give the exact paths and a snapshot or a way to verify the recorded contents, such as hashes or a scoped diff with any new file contents. Ask the recipient to confirm this state before acting.
- For a different workspace, give an accessible base and cover every scoped input the recipient needs. Use a patch with its base and any required new files, an accessible snapshot, or excerpts that cover the requested scope. Include only material the recipient is allowed to see. Mark missing inputs and tell the recipient what to obtain before starting. Use the available artifact or supplied context for work without Git.

## Write the brief

Write directly to the recipient. Put the requested outcome first, followed by the starting point or review target, files to read, scope, and expected response. Include only relevant context the recipient is allowed to see. Distinguish observed checks and results from checks the recipient should perform.

- **Review** names the exact change or artifact, intended behavior, review focus, and known verification gaps. Default to a read-only review. Request prioritized findings with locations, evidence, and the consequences of each issue. Honor any editing scope the user explicitly requests.
- **Implement** states what to build or finish, which decisions and constraints apply, what is already done, and what remains. Include acceptance criteria, relevant dependencies, and how to verify the result. Request the completed artifacts, checks actually run, and any remaining blockers.

The receiving agent follows its own applicable project instructions and permissions. Check that the brief makes sense on its own and that its references and stated results match the available evidence. Use the bundled template when helpful. Fill or remove every placeholder and keep the selected mode's section. [Brief template](assets/brief-template.md)

## Deliver it

Return a copyable Markdown brief in the conversation. Save a file when requested, using the user's path or a distinct filename in a suitable project location. Preserve unrelated contents, report the path if saved, and include a short copyable starter prompt pointing the receiving agent to that file (unless the user asked for file-only output). If writing is unavailable, return the brief as text and say it is unsaved.
