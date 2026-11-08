# Repository cleanup

Explicitly invoke `cleanup` for a repository-wide or targeted maintainability sweep. It maps the relevant areas, gathers evidence, prioritizes findings, applies clear fixes that preserve behavior, and verifies the result. Larger decisions come back for discussion unless already settled.

Discussing or developing the skill does not start a cleanup sweep. Ordinary implementation and review continue using the relevant skills and their existing scope.

## Scope and requests

The default sweep considers duplication, unnecessary complexity, obsolete material, file structure and module boundaries, tests, documentation, configuration, and evidenced performance costs. It follows existing project conventions and preserves intentional duplication, including independently installed components and required attribution files.

A full sweep accounts for the relevant authored areas, with inspection depth matched to the repository and available resources. The result identifies what was inspected, sampled, and skipped. It does not imply every file or execution path was examined.

Qualify the request in ordinary language; these are examples rather than required command flags:

- "Use cleanup across this repository. Fix clear issues and bring larger changes back for discussion."
- "Use cleanup to audit the repository and return prioritized findings only. Do not edit files."
- "Use cleanup on the API and tests, focusing on duplicated validation and module boundaries."
- "Use cleanup for a first pass focused on configuration and documentation. Use subagents if available and permitted."

Findings-only requests keep repository files unchanged. A normal cleanup request already authorizes clear local fixes within its scope; it does not require approval of every finding. Architectural changes, intended behavior changes, public contracts, dependency upgrades, instruction-policy changes, and external actions follow the user's actual authorization.

The skill preserves unrelated work and checks whether apparently unused material has dynamic, exported, configured, or packaged consumers before removing it. Performance findings need measurements or a demonstrable cost; suspected bottlenecks remain labeled hypotheses.

## Coordination and related skills

For a larger repository, complementary workers can inspect areas such as implementation, tests, tooling, and documentation, or focus on a concern spanning several areas. Initial investigation is read-only. The owner verifies and combines findings, resolves cross-area recommendations, and assigns clear ownership before implementation. When workers are unavailable or prohibited, the same work proceeds directly and sequentially.

Every helper is optional; cleanup includes enough guidance and its own bundled sweep guide to work independently.

| Skill | Contribution |
| --- | --- |
| interview | Resolve consequential goals, constraints, or design choices. |
| orchestrate | Coordinate areas, worker lifecycles, integration, and completion. |
| task-plan | Keep coverage, decisions, and progress when continuity benefits. |
| repo-style | Guide discoverable structure and concise documentation. |
| fresh-review | Review the integrated result in a separate context when possible; otherwise label self-review. |
| approval-gate | Resolve a new authorization boundary using the concrete proposed action. |
| git-style | Prepare coherent Git changes when Git operations are requested. |
| setup | Separately record durable workflow preferences when explicitly requested; cleanup does not invoke it. |

## Result and completion

Expect a concise account of coverage, completed improvements and their reasons, remaining findings with evidence and next steps, and checks actually performed. Verification and review limitations stay explicit. A clean area can have no actionable findings.

The sweep ends when its bounded coverage and authorized changes are complete and applicable checks are satisfied. It can report deferred decisions without repeatedly searching for more work or creating a new tracking system. Report files, branches, commits, and publication are conditional on the task and project conventions.

See [installation](installation.md) for invocation examples and [compatibility](compatibility.md) for manual-selection controls and behavioral checks.
