---
name: task-plan
license: Apache-2.0
description: Plan work and keep a resumable record of goals, decisions, assignments, and progress. Use when the user asks for a plan or when substantial, delegated, or multi-session work needs a durable handoff. Supports conversation and project files without requiring Git.
---

# Task plan

Use the smallest record that makes the work clear. A short task can use a few conversational steps. Save a record when requested or when it helps coordinate assignments or carry work across context compaction or sessions.

## Choose the medium

- Honor the requested format and location or the project's conventions. Reuse the matching record when one exists.
- When a new record belongs in the project and there is no chosen location, save one Markdown file per overall task at `tasks/<task>.md` under the project root. Create the directory as needed and choose a distinct, descriptive filename.
- When writes are unavailable or outside the task's scope, keep a textual checkpoint and identify it as unsaved.
- Follow existing Git rules and the project's preference for local or shared records. Change ignore rules or include records in commits only when authorized.
- Do not require Git, a branch, a pull request, or a formal specification. If a spec is requested or already exists, link to it instead of replacing it.

## Record what matters

Use [assets/plan-template.md](assets/plan-template.md) when helpful. Keep only applicable sections:

- State the **outcome** and how to recognize success.
- Capture relevant **context and constraints**, including facts, instructions, and boundaries.
- Define **work items** with stable names, concrete outcomes and completion conditions, assignees when applicable, and any dependencies. Track each item's status as pending, in progress, blocked, or done. Link longer briefs and relevant artifacts when useful.
- Record confirmed **decisions** and reasons for significant changes. Label assumptions and open questions.
- Keep a **checkpoint** with the current state, next action, and any blockers.
- Record **verification** methods and observed results.
- Describe **follow-ups** outside the task with a brief finding, evidence or location, and next step. Ask before adding them to an existing tracker unless already authorized. Otherwise report them in the conversation. Authorization for follow-up work remains subject to the task's scope.

Add domain-specific sections only when they help, such as a data migration, publication wording, experiment design, or release steps. An interview skill can help clarify decisions but is not a prerequisite.

A plan records intent; it does not grant permission to execute every proposed action.

## Keep it current and transferable

Capture the initial breakdown and next action before substantial work or dispatch. Share the path when you save a record. In handoffs, pass the saved path if the recipient can open it or a self-contained checkpoint if they cannot.

The coordinating agent owns edits to the task record. For delegated work, save any worker or output references needed to resume it or collect the result as they become available. Workers report results, checks, and blockers against their work item.

Update assignments, decisions, and progress as they change. Mark an item done once you have evidence that it meets its completion condition. Record the result and supporting evidence in the same update. For blocked work, state what would unblock it. Keep the next action visible and refresh the checkpoint before a pause or handoff.

After compaction or when resuming in another session, reopen the matching record from its known path or look for it in the project's chosen location or `tasks/`. Use an available checkpoint if the file is inaccessible. Reconcile the recorded state with current instructions, artifacts, checks, and observable worker state before continuing or retrying unfinished work.

At completion, record the result and checks that actually ran. Identify outstanding decisions and follow-ups. Include the saved path or checkpoint text in the final handoff based on what the recipient can access. Use a merge or publication status only when that event was part of the task and occurred.
