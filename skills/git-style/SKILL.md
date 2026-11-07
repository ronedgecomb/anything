---
name: git-style
license: Apache-2.0
description: Prepare focused Git changes and clear commit messages, using Conventional Commits when the project has no other convention. Use when organizing a change, preparing a commit, or discussing Git workflow. Follow project branch and integration rules, and perform commits or remote actions only within the user's authorization.
---

# Git style

Follow the user's request and applicable project conventions. When no commit-message convention is established, use [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/).

This skill needs Git only for Git operations. Without repository access, help draft the proposed change or message. Do not initialize a repository or install tools as a side effect.

## Understand the state

Inspect the relevant repository status, changes, and recent history when available. Identify the intended scope and existing conventions. Preserve unrelated edits and user work.

Choose branch and integration behavior from the task and project. This skill does not require a feature branch, worktree, merge commit, squash, or pull request.

## Prepare focused changes

- Keep each commit coherent enough to understand and review on its own.
- Stage only intended changes, using explicit paths or selected hunks as needed. Do not scoop up unrelated changes.
- Include necessary tests and documentation with the behavior they explain.
- Verify the affected result using the project's applicable checks. Report meaningful limits and unrelated failures.
- Do not fabricate an author, signature, issue reference, or attribution trailer. Use configured identity and required project metadata.

Preparing a change or message does not itself mean the user asked you to commit it.

## Write the message

Use this form by default:

```text
<type>[optional scope][!]: <summary>

<optional explanation>

<optional footers>
```

Use a short, concrete summary of the change. Include a scope when it helps identify the affected area. Explain the reason or non-obvious consequence in the body.

- `feat` introduces a feature; `fix` corrects a bug.
- Other useful types include `docs`, `refactor`, `test`, `perf`, `build`, `ci`, and `chore`. Follow the project's type set when it has one.
- Mark a breaking change with `!` before the colon or a `BREAKING CHANGE:` footer, and explain the compatibility impact.
- Add issue references and trailers only when applicable. Do not treat a local formatting preference as a requirement of the specification.

Examples:

```text
feat(search): filter results by tag
fix(parser): handle an empty input
docs: explain local installation
```

## Execute and report

Commit, push, publish, merge, rewrite history, or delete branches only when authorized for that effect. Reuse authorization within its scope; clarify a material change rather than re-asking about the same action. An approval-gate skill can help if installed, but is not required.

Respect protected branches and project integration policy. Avoid rewriting or discarding unrelated work. Cleanup needs its own applicable authorization and ownership check.

Verify the actual repository or remote result when an action is performed, then report it accurately. Do not claim a commit, push, or merge when you only prepared its contents.
