---
name: task-plan
license: Apache-2.0
description: Create or maintain a concise plan, decision record, and handoff for a task when complexity, collaboration, or continuity benefits from one. Use when the user asks for a plan or when coordinating substantial work across steps or sessions. Supports conversation, project files, and non-code work without requiring Git.
---

# Task plan

Use the smallest record that makes the work clear. Follow the user's requested format and existing project practice. A short task can use a few conversational steps; a task spanning sessions may need a saved plan.

## Choose the medium

- Reuse an existing plan or the project's chosen record location.
- When a new file is useful and writing is permitted, use a descriptive name in an appropriate project directory. `tasks/<task>.md` is one option, not a requirement.
- Without writable files, return the plan as text and identify it as unsaved.
- Leave tracking and ignore policy unchanged unless the user or project calls for a change. Do not assume a plan must be private, ignored, or committed.
- Do not require Git, a branch, a pull request, or a formal specification. If a spec is requested or already exists, link to it instead of replacing it.

## Record what matters

Use [assets/plan-template.md](assets/plan-template.md) when helpful. Keep only applicable sections:

- **Outcome:** the requested result and how to recognize success.
- **Context and constraints:** facts, relevant instructions, boundaries, and dependencies.
- **Approach:** actionable steps at the right scale, with owners only when work is delegated.
- **Decisions:** confirmed answers and their consequences, separated from assumptions and open questions.
- **Progress:** completed work, current state, the next step, and actual blockers.
- **Verification:** checks or review methods appropriate to the artifact and their observed results.
- **Follow-ups:** work that remains outside this task, placed in the project's normal tracker when appropriate.

Add domain-specific sections only when they help, such as a data migration, publication wording, experiment design, or release steps. An interview skill can help clarify decisions but is not a prerequisite.

A plan records intent; it does not grant permission to execute every proposed action.

## Keep it current and transferable

Update the record when a material decision or state changes. Preserve the reason for significant revisions without copying the whole conversation.

Give a worker or another session the relevant content and current status. A path is sufficient only when that recipient can actually access it. Otherwise provide a self-contained snapshot or a permitted artifact transfer. Do not assume shared memory or a shared filesystem.

At completion, record the result and checks that actually ran. Identify outstanding decisions and follow-ups. Use a merge or publication status only when that event was part of the task and occurred.
