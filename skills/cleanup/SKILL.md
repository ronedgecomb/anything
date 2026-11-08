---
name: cleanup
license: Apache-2.0
description: Sweep a repository for duplication, unnecessary complexity, structural problems, and maintainability improvements. Use only when the user explicitly invokes cleanup or requests a repository cleanup sweep. Never select this skill automatically for ordinary implementation or review.
disable-model-invocation: true
---

# Cleanup

Run only after an explicit cleanup request. Discussing, implementing, or reviewing this skill does not invoke it. If loaded without a cleanup request, return to the user's task without starting a sweep.

Own a bounded repository sweep from discovery through verification. By default, fix clear issues that preserve behavior and discuss larger changes. Honor a request for findings only. This skill works on its own and does not require code, Git, subagents, or another installed skill.

## Establish the scope

1. Identify the target repository or requested areas, the user's goals, and any focus, exclusions, or resource limits. Ask about consequential unknowns; use the existing context for settled choices.
2. Read applicable project instructions and entry points. Map the relevant source, tests, documentation, configuration, tooling, and their boundaries. Follow the existing organization unless a change solves a concrete problem.
3. Inspect the current work when available. Preserve unrelated edits, untracked files, and user data; their presence does not make them cleanup candidates.
4. Identify useful existing checks and record relevant baseline failures when practical. Avoid checks with unapproved effects. If execution or file access is limited, continue with the accessible evidence and state the limits.
5. Use a plan or coverage record at the scale the work needs. The conversation can hold it; a broad or interrupted sweep may benefit from an existing project record. Do not require a new report, tracker, branch, or worktree.

Without writable files, return findings and proposed edits as text and state that nothing was saved.

A full sweep covers the relevant authored areas of the repository. Generated output, vendored code, external repositories, and ignored or sensitive material are normally excluded unless the request and project context make them relevant. Record what was inspected, sampled, or skipped, with meaningful limits. A targeted request narrows the sweep to its named areas or concerns.

## Inspect for concrete improvements

Use the applicable lenses in [references/sweep-guide.md](references/sweep-guide.md). Start with read-only investigation so proposed changes reflect the repository as a whole. Trace related patterns across areas before deciding what to consolidate.

- Look for repeated logic or configuration, unnecessary complexity, obsolete material, unclear boundaries, misplaced files, brittle tests, stale documentation, and evidenced performance costs.
- Tie each candidate to a practical consequence: inconsistent fixes, avoidable coupling, difficult navigation, fragile changes, wasted resources, or another observable maintenance problem. Separate facts, hypotheses, and preferences.
- Preserve intentional duplication where it supports independent installation, distinct behavior or ownership, fixtures, examples, generated sources, or required license and attribution files. Similar text alone does not justify a shared abstraction.
- Before removing apparently unused material, check relevant entry points, exports, dynamic loading, configuration, scripts, packaging, and compatibility obligations. An empty reference search is evidence to investigate, not proof of disuse.
- Support performance work with a relevant measurement or a concrete, demonstrable cost. Label suspected bottlenecks as hypotheses and avoid speculative optimization.

Useful outcomes include confirming that an area needs no change. Do not invent findings, impose a preferred architecture, or optimize for fewer lines or files.

## Delegate when useful and permitted

Use subagents when the available capabilities, permissions, and task size support them. Otherwise perform the same sweep directly, sequencing the relevant areas. Delegation is optional.

- Split by repository area or complementary focus, such as implementation, tests, configuration, and documentation. Keep responsibility for patterns that cross those boundaries with the integration owner.
- Give each worker a bounded brief with accessible inputs, applicable instructions, scope, resource limits, and evidence requirements. The sweep guide includes a self-contained brief.
- Prefer read-only investigation first. Assign implementation after triage, with clear ownership; sequence overlapping edits and checks that share mutable resources.
- Collect actual results and completion status. Verify important claims, combine duplicate findings by root cause, and resolve conflicting recommendations before applying changes. Reviewer agreement is not proof.

Use subprocess workers only when suitable tooling is already available, permitted, and supports collecting results, tracking completion, and stopping the processes you start. Never use a fallback to bypass a delegation restriction or install tooling merely to obtain workers.

## Triage and apply changes

For each worthwhile finding, establish its location and evidence, maintenance consequence, proposed correction, likely impact and risk, and a useful verification method. Prioritize concrete benefit relative to disruption and effort. Keep the actionable set focused; report uncertain or low-value ideas accordingly.

- **Findings only:** Return the prioritized findings and suggested next steps. Keep repository files unchanged, including through formatters or other checks with write effects.
- **Clear fixes:** Apply authorized changes in coherent batches. Preserve observable behavior, public interfaces, data formats, supported compatibility, and required attribution. Update affected references, tests, and documentation together.
- **Larger decisions:** Present concrete options and trade-offs for changes to architecture, intended behavior, public contracts, new dependencies, or other consequential boundaries that the user has not already authorized. Continue independent work while the decision is open.
- **Defer:** Report out-of-scope or unsupported ideas with available evidence and a next step. Ask before adding them to an existing tracker unless already authorized; otherwise use the conversation.

An explicit cleanup request can already authorize routine local fixes throughout its stated scope. Do not ask again for every finding. Broader product work, dependency upgrades, instruction-policy changes, tool installation, and Git or external actions need authorization appropriate to those effects. Ordinary cleanup does not invoke setup.

Keep diffs focused. Avoid unrelated formatting churn and premature abstractions. Treat file moves as changes with consumers: check imports, paths, discovery rules, packaging, and documentation. Do not remove meaningful tests merely to make a check pass.

## Verify and finish

Run checks appropriate to the affected artifacts and project rules. Reuse existing coverage; add or update tests when they give meaningful confidence in preserved behavior or a relevant failure. Broaden verification when shared changes or project requirements justify it. Distinguish baseline failures from regressions and explain checks that could not run.

Review the integrated result for unintended behavior changes, broken references, lost coverage, and new coupling. Use a separate review context when useful, available, and permitted; otherwise label the review as self-review. Do not claim independent review or runtime verification that did not occur.

Report:

- Coverage: areas inspected, sampled, or skipped and material limitations.
- Changes: the useful improvements actually made and why.
- Remaining findings: priority, evidence or location, and the decision or next step needed.
- Verification: checks actually performed, their results, review independence, and any remaining uncertainty. Distinguish measured performance changes from expected benefits.

Finish when the bounded sweep and authorized changes are complete and applicable verification is satisfied, or clearly identify outstanding requirements. Do not repeat sweeps solely to find more work or require a repository with zero possible improvements.

When installed and useful, interview, orchestrate, task-plan, repo-style, fresh-review, approval-gate, and git-style can support the corresponding stages. Apply the guidance above directly when they are unavailable. Setup remains a separate, explicitly requested configuration task.
