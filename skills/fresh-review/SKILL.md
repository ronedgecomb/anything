---
name: fresh-review
license: Apache-2.0
description: Review code, documents, research, plans, or other artifacts for concrete problems and useful improvements. Use when the user asks for review or when consequential work benefits from a separate perspective. Prefer a separate review context when available and permitted; otherwise perform and clearly label a self-review.
---

# Fresh review

Judge the artifact against the requested outcome and available evidence. Follow project expectations and scale the review to the work. This skill does not require a branch, plan file, or another installed skill.

## Establish the target

Identify the artifact, intent, applicable constraints, and the questions that matter. Use a stable copy, version, or snapshot when possible. If work changes during review, state what version was reviewed and revisit affected findings.

For code, inspect the relevant change and surrounding behavior using the available comparison tools. For writing, research, or plans, check the argument, evidence, audience, omissions, and internal consistency.

## Choose the review context

- Use a separate reviewer when supported, permitted, and useful. Give it the artifact and intent without steering it toward your expected findings.
- For independent review, choose a reviewer that did not author the artifact and minimize inherited implementation discussion. Disclose limits when the environment cannot separate that context.
- Choose review lenses based on the actual risks. One focused reviewer may suffice; add a security or other specialist perspective when justified.
- A permitted subprocess worker is an option only when suitable tooling and lifecycle controls are available. Never use it to bypass a restriction on delegation.
- Without a separate context, deliberately re-examine the artifact yourself. Label this self-review and acknowledge its limits.
- If independent review is explicitly required and cannot be obtained, provide a handoff brief and state that the independent review remains outstanding. Do not substitute self-review while claiming that requirement is complete.

The bundled [code-review brief](references/code-review-brief.md) and [security-review brief](references/security-review-brief.md) are optional examples. Adapt them or prepare a brief for another domain.

## Gather findings

Keep the reviewed artifacts unchanged during review. Run checks only when permitted and their effects are understood; avoid conflicting use of shared resources.

Each finding should include:

- Its importance and the concrete consequence.
- Evidence, such as a file and line, section, source, calculation, or observed behavior.
- A failure scenario or explanation of why the result misses its goal.
- A proportionate correction.

Separate confirmed defects, unresolved questions, and preferences. Verify a finding before accepting it; agreement between reviewers is not proof. Identify unnecessary complexity or brittle verification where it has a practical cost, and avoid inventing issues to fill a report.

## Triage and follow through

| Decision | Action |
| --- | --- |
| Fix | Correct a substantiated issue within the requested scope and authorization. |
| Record a trade-off | Explain the consequence of an intentional choice in an appropriate existing record. |
| Follow up | Defer out-of-scope work with a brief finding, evidence or location, and next step. Ask before adding it to an existing tracker unless already authorized; otherwise report it in the conversation. |
| Reject | Give a concise evidence-based reason. |

Do not silently change an explicitly settled product decision or locked wording to satisfy a reviewer. Explain the conflict when it needs a new decision.

An unrelated finding does not authorize further investigation, fixes, or delegation. Ask before expanding the task, or report it for later without creating a tracking system.

After fixes, verify the affected result. Repeat a wider check when the project requires it or the change justifies it. A second specialist review is useful when a significant risk remains, not a mandatory phase for every correction.

Report the meaningful findings, what changed, remaining concerns, what was checked, and whether the review used a separate context. Put the result in the conversation or an existing artifact as appropriate; do not require a pull request or a new report file.
