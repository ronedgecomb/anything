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

Evaluate consequences rather than location alone. A remote read can be routine; a local deletion can destroy important work. Pushing a branch, sending a message, merging, publishing, and deleting resources each need authorization appropriate to their actual effect; none is automatically included in an unrelated action.

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
