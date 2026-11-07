# Brief templates

Adapt the brief to the task and actual capabilities. Fill or remove every placeholder. Use the relevant parts yourself when no worker can be started.

A worker needs enough context to succeed without assuming that it shares the conversation, filesystem, or memory.

## General handoff

```text
Role: <investigate | research | draft | implement | document | review>.
Outcome: <the concrete result needed>.

Context and inputs:
- <Relevant task intent, facts, and confirmed decisions.>
- <Source content, an accessible artifact snapshot, or a path the recipient can read.>
- <Applicable project instructions.>

Scope and boundaries:
- Own <artifacts, area, or resources>.
- <What other work is happening, if relevant.>
- Stay within <permissions, cost, time, and tool limits>.
- <Actions that are out of scope or reserved for the integration owner.>

Work:
1. <A bounded task.>
2. <A relevant check and the expected evidence.>

Report:
- The result or returned artifact, with its location if actually saved.
- Evidence and checks actually performed.
- Assumptions, limits, and unresolved questions.
- Any changes or side effects.
```

## Investigation or research

Give a focused question and the sources the worker may access. Ask it to distinguish observations from inference. Request source locations, quotations, or other evidence when useful; do not require file-and-line references for material that has no files.

Use complementary questions rather than duplicating the same search. Findings can include constraints and possible approaches when that is the requested work.

## Drafting or implementation

State the intended behavior or audience, ownership boundaries, and verification criteria. When another contributor produces a dependency, state its expected interface and availability.

Require a branch, workspace, commit, or trailer only when the project and task actually call for it. Do not invent repository conventions. Keep external actions within the worker's explicitly assigned authorization.

## Documentation

Describe the intended reader and which artifact or behavior is authoritative. Ask the worker to verify factual claims and report contradictions. Update the existing documentation that needs the change; do not require a separate docs agent or a new guide for every task.

## Follow-up

Reuse the worker's context only if the environment supports it. Otherwise provide the relevant original context and the current artifact again.

```text
The current result is <artifact or snapshot>.
These findings were accepted: <findings and the evidence>.
Apply or investigate <bounded follow-up>.
Preserve <confirmed constraints or explicitly locked wording>.
Verify <affected checks>.
Return the actual result and any remaining limits.
```

A plan, review, or prior handoff is context, not a source of extra permissions.
