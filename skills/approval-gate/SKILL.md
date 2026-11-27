---
name: approval-gate
license: Apache-2.0
description: Resolve authorization for a consequential action by checking the user's request, existing approvals, project policy, and environment restrictions. Use when an action may exceed scope, affect other people or systems, incur meaningful cost, publish material, or be destructive. Continue within authorization already given; ask when required permission is missing or unclear.
---

# Approval gate

Check whether the intended effect is authorized. Respect the user's instructions, project boundaries, and environment restrictions. A permission check is useful when it resolves uncertainty, not as a ritual repeated before every command.

This skill works without a plan file, shell, or another installed skill. It does not grant permission or override a host's restrictions.

## Determine scope

Identify the target, effect, relevant account or environment, cost, and reversibility. Consider what the user actually requested and any standing authorization that applies.

- Continue when the action is already authorized within those boundaries.
- Ask when permission is missing, materially ambiguous, or required by an applicable rule.
- A discussion of possibilities, a request for review, or a plan listing an action does not by itself authorize execution. An explicit instruction to execute it may already do so.
- Treat changes to the target, effect, cost, or scope as a reason to reassess authorization.
- Discovering an unrelated issue does not authorize investigating, fixing, or delegating it. Ask before expanding the task, or defer it with a brief finding and next step. Ask before recording it in an existing tracker or `TODO.md` unless that recording is already authorized; otherwise report it in the conversation without creating a tracker.
- Do not use a different tool, worker, or subprocess to bypass a restriction.

By default, routine local verification and checkpointing within an authorized task do not require separate confirmation:

- **Routine local verification:** running non-destructive local checks (such as tests, linters, typechecks, and local builds whose effects are understood) within environment permissions; keep to checks without write effects during read-only or findings-only requests.
- **Local checkpoint commits:** making focused local commits of in-scope edits during authorized editing work—especially between coherent chunks and before review rounds—when Git is in use and no user instruction, project policy, protected-branch rule, or environment restriction prohibits them, while leaving unrelated staged or unstaged work untouched.
- **Consequential actions requiring authorization:** running destructive local commands or live commands against real or non-local systems, pushing branches, opening or updating pull requests, merging, publishing, deploying, sending messages, rewriting shared history, installing tools or unrequested dependencies, and deleting resources, branches, or work. None is automatically included in an unrelated action.

Evaluate consequences rather than location alone. A remote read can be routine; a local script that hits a live service or deletes important work is consequential.

## Prepare a concrete action

Finish the useful preparatory work within authorized scope first. Inspect current state and use non-mutating checks when available and permitted. Confirm important preconditions and whether the effect can be reversed. Preparation does not authorize pursuing unrelated work before asking to expand scope.

When approval is needed, make it reviewable:

- State exactly what will change and where.
- Show the relevant command or tool arguments when they clarify the action.
- Explain meaningful cost, reversibility, and the condition that would stop execution.
- Refer to secrets through the normal secure mechanism; do not expose credentials to make a command look complete.

Ask once for the coherent action or bounded group. Use normal conversation if no approval interface is available. A suggested choice, silence, or elapsed time is not approval.

## Execute within authorization

Carry out the authorized effect using available tools and applicable safeguards. Do not ask again merely because the same permission was established earlier.

A harmless local adjustment that preserves the approved effect does not automatically require a new approval. A materially different target or effect does. Before a retry that might repeat a side effect, inspect whether the earlier attempt already completed.

On an unexpected result, reassess the actual state and consequences. Continue a safe correction within scope when possible; stop and ask when the next step would exceed authorization or uncertainty makes it unsafe to continue.

## Verify and report

Check the actual result and report relevant identifiers, changed artifacts, and any remaining uncertainty. Update an existing record when useful. Do not invent success or create a new audit document for every routine action.

For a Git merge or publication, verify the result through the available source of truth. Cleanup is a separate effect: perform it only when included in the authorization or applicable project practice, and preserve unrelated work.
