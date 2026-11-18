---
name: using-anything
license: Apache-2.0
description: Choose which anything skills to read and apply for the current task. Use when starting substantial work, deciding between overlapping skills, or combining skills as the task changes. Setup, cleanup, and handoff require explicit user requests.
---

# Using anything

Choose the smallest useful set of skills for the user's requested outcome. Follow the user's instructions, applicable project conventions, and the current environment's restrictions. This guide and the skills it describes do not grant additional permissions.

Each skill works independently. This guide is optional, and the skills below may be installed individually or unavailable in the current session.

## Discover and read

1. Identify the requested outcome, current stage, and scope from the available context. Honor explicitly requested skills and modes, including findings-only reviews and drafts without edits.
2. Consult the current session's skill catalog or available descriptions. Use the map below to distinguish likely candidates, then check their actual availability and invocation controls. A name in this guide is not evidence that a skill is installed.
3. Read a selected skill's full instructions before applying it. Load only the supporting files needed for the current work, resolving paths relative to that skill's directory. Avoid loading every skill or reference merely because it is listed.
4. Apply relevant guidance within the task's scope. When a helper is unavailable, continue directly using the accessible instructions and task context when that is sufficient. Report missing guidance when it affects the result; clarify the next step if an explicitly requested skill's instructions are essential and inaccessible. Do not claim to have applied unread instructions or install skills or tools as a side effect of selection.
5. Reassess selection when the work changes stage, new evidence changes the approach, or the user redirects it. Preserve settled decisions and authorization within their scope.

## Choose by need

| Need | Skill | When and how it helps |
| --- | --- | --- |
| Clarify a topic, goal, decision, or requirements | `interview` | Use when the user asks for an interview or consequential uncertainty needs conversation. Inspect context first and ask about choices that affect the result; routine reversible choices can be made directly. |
| Coordinate work across steps, areas, or contributors | `orchestrate` | Use when sequencing, dependencies, integration, or handoffs need attention. It owns execution through completion; direct work is a complete option and delegation depends on capabilities and permission. |
| Keep a plan, decisions, progress, or a handoff | `task-plan` | Use when requested or when work needs a durable record across assignments, compaction, or sessions. Use the conversation for short tasks and the project location or `tasks/` for saved records. |
| Prepare a brief the user will pass to another agent | `handoff` | Use only after an explicit request to prepare a review or implementation handoff. Return a copyable brief for the user to transfer. |
| Evaluate code, writing, research, plans, or other artifacts | `fresh-review` | Use for a requested review or when consequential work benefits from another perspective. Use a separate context when useful and permitted, and label self-review accurately when reviewing your own work. Preserve findings-only scope. |
| Resolve authorization for a consequential action | `approval-gate` | Use when scope, effects, cost, reversibility, or an applicable approval boundary need attention. Check the request and existing authorization; continue within it and ask when required permission is missing or unclear. |
| Organize Git changes or prepare commit messages | `git-style` | Use for focused changes, project Git conventions, and commit preparation. Commits, pushes, pull requests, merges, history changes, and branch cleanup each depend on authorization for their effect. |
| Add or organize files, project structure, or documentation | `repo-style` | Use to find appropriate homes, maintain useful entry points, and document supported behavior. Follow the existing organization and add structure when it solves a concrete problem. |
| Keep affected code, tests, comments, and prose focused on current requirements | `no-tombstones` | Use during ordinary creation, modification, review, and cleanup. Remove or rewrite residue without a current purpose within scope; preserve meaningful regression coverage, compatibility, and necessary migration or historical guidance. |
| Initialize or update durable project workflow preferences | `setup` | Use only after an explicit setup or project instruction configuration request. Preserve existing instructions and record settled project preferences; ordinary tasks can use defaults immediately. |
| Sweep a repository for maintainability improvements | `cleanup` | Use only after an explicit cleanup invocation or repository sweep request. Bound the sweep, fix clear issues that preserve behavior, and discuss larger changes. A findings-only request keeps files unchanged. |

Use setup, cleanup, and handoff only when their work is explicitly requested. Treat discussion, authoring, and review of these skills as reference.

## Combine and sequence

Start with the skill that addresses the main need. Add another when it contributes useful guidance to the actual task. Overlapping advice alone does not justify loading more instructions, and a task can be completed with one skill or directly without this guide.

Keep these responsibilities clear:

- `using-anything` helps select guidance, `orchestrate` coordinates execution, and `task-plan` maintains the working record. On explicit request, `handoff` prepares a brief the user can transfer.
- `repo-style` guides organization and documentation. `no-tombstones` applies across affected code, tests, and prose. Both can support a focused edit without starting a repository sweep.
- `fresh-review` evaluates the target artifact. `cleanup` owns an explicitly requested sweep and its authorized fixes. A review finding alone does not authorize edits or a broader sweep.
- `approval-gate` resolves permission for an effect. Selecting it does not require another approval when the action is already authorized, and selecting any other skill does not authorize its possible external actions.

Order the work by its dependencies. Clarify a blocking decision before implementing it, keep a plan when continuity needs one, and review and verify the resulting artifact at an appropriate scope. Git and publication steps belong only to tasks that call for them. There is no required sequence through the whole collection.

## Examples

These examples assume the named skills are available and useful. Apply the current skill directly when a suggested helper is absent.

| Request or situation | Selection and scope |
| --- | --- |
| Update documentation after replacing a module | Use `repo-style` for clear current usage and `no-tombstones` for affected explanations of the previous implementation. Preserve migration instructions when readers still need them. |
| Review a research draft and return findings only | Use `fresh-review` to check the argument, sources, and omissions. Return evidence and suggested corrections while leaving the draft unchanged. |
| Deliver a change with dependent parts across several sessions | Use `orchestrate` for sequencing and integration, and `task-plan` for decisions, status, and handoff. Add an interview or review when a specific uncertainty or risk calls for it; execute directly when delegation is unavailable or prohibited. |
| Commit a change the user has already approved for commit | Use `git-style` for the focused commit and configured identity. Continue within that authorization; reassess permission if the target or intended effect materially changes. |
| Notice unrelated duplication during a focused fix | Keep the current scope and report the finding with available evidence and a next step. Use `cleanup` for a sweep only if the user explicitly requests one. |
| Only this guide is installed | Use the map to understand relevant concerns and carry out the task directly within available guidance. Sibling skills and root repository documents are optional. |

## Check the selection

Confirm that the chosen guidance fits the requested outcome and mode, the instructions you rely on were accessible and read, and any supporting work stays within scope. Perform the checks appropriate to the resulting artifact and report actual results and meaningful limits. A separate selection report or plan file is optional.
