# Sweep guide

Choose lenses that fit the repository and request. Inspect enough surrounding context to assess a candidate's consequences. Use the same questions for direct work or a delegated investigation.

## Review lenses

| Lens | Look for | Before recommending a change |
| --- | --- | --- |
| Duplication and consolidation | Repeated behavior, diverging copies, parallel configuration, competing sources of truth. | Check that the copies have the same semantics and should change together. Weigh the shared dependency and coupling against the maintenance benefit. Preserve independent packaging, required notices, fixtures, and intentional variation. |
| Complexity and clarity | Deep branching, unclear names, mixed responsibilities, unnecessary layers, excessive indirection, oversized modules. | Identify a concrete comprehension or change cost. Prefer an existing pattern or a simple local improvement before adding an abstraction. |
| Obsolete or unused material | Dead paths, stale flags, obsolete compatibility code, unused dependencies, abandoned documentation. | Trace exports, dynamic consumers, scripts, configuration, packaging, supported versions, and documented use. Search results alone do not establish that removal is safe. |
| Structure and boundaries | Misplaced files, unclear entry points, circular dependencies, accidental coupling, confusing module ownership. | Follow the project's conventions. Explain how the move or boundary change helps readers or callers, and identify affected paths, discovery rules, and imports. |
| Tests and verification | Duplicate coverage, brittle implementation assertions, slow redundant setup, missing checks around a proposed refactor. | Preserve required behavior coverage. Distinguish redundant tests from cases exercising different contracts; add focused coverage where the change needs confidence. |
| Documentation and configuration | Stale examples, broken local links, contradictory instructions, drift between tooling and documented commands. | Establish the authoritative source and actual supported usage. Keep useful entry points concise and update their consumers together. |
| Tombstones | Explanations, comments, or tests whose only purpose is memorializing or forbidding a previous implementation. | Identify a concrete current requirement or reader need before retaining historical references or absence checks. Preserve meaningful regression coverage and necessary migration guidance. |
| Performance and resources | Repeated expensive work, avoidable I/O, unnecessary allocation, missing resource cleanup, clearly inefficient algorithms. | Establish a representative measurement or demonstrable cost and preserved behavior. Report hypotheses honestly; check that added complexity is justified. |

## Finding format

Use a concise structure that supports a decision; a table or prose is enough:

- **Finding and priority:** the concrete problem and its relative importance.
- **Evidence:** accessible paths and locations, an observed result, or another verifiable source; distinguish inference.
- **Consequence:** how it affects maintenance, supported behavior, or resource use.
- **Correction:** the smallest useful change, including why intentional variation remains intact.
- **Risk and verification:** affected consumers or contracts, uncertainty, and a proportionate check.
- **Disposition:** fixed, proposed for discussion, deferred, or rejected with a reason.

Group multiple symptoms of the same root cause. Verify findings before accepting them. A report with no actionable finding is valid; do not require a finding count or a particular severity.

## Investigation brief

Adapt the brief and fill or remove placeholders. Give workers the relevant content when they cannot access a local path. The integration owner retains cross-area decisions.

```text
Outcome: Identify worthwhile cleanup opportunities in <area or focus>.

Inputs:
- <Accessible repository snapshot or relevant content.>
- <Project purpose, instructions, supported contracts, and known baseline issues.>

Scope:
- Inspect <owned area> through <selected lenses>.
- Respect <exclusions, permissions, and resource limits>.
- Investigate without changing files or running checks with write effects.
- Other workers cover <adjacent areas>; report cross-area candidates to the owner.
- Do not expand into unrelated work or start further workers without authorization.

Report:
- Areas inspected, sampled, or skipped, and limits on coverage.
- Prioritized findings with evidence, consequence, proposed correction, risk,
  and a relevant verification method. Distinguish facts from hypotheses.
- Intentional duplication or boundaries that a proposed consolidation must preserve.
- Checks actually performed, results, and any side effects.
- Unresolved questions or no actionable findings, as applicable.
```

For implementation, replace the read-only boundary with the specific accepted findings, owned files or resources, preserved contracts, and required checks. Establish ownership before allowing concurrent writes. A brief cannot expand the user's authorization.
