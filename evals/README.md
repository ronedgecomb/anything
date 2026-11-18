# Optional behavioral evaluations

Use [cases.json](cases.json) to replay a small set of behavioral checks when changing a skill. These evaluations are optional, run on demand, and require no new runtime dependency. They are not part of skill installation or a mandatory CI job. The [compatibility checks](../docs/compatibility.md#behavioral-checks) remain the broader contract; this catalog is a starting sample.

The fixtures are synthetic and bundled in the catalog. Run them in an isolated scratch workspace, never against a real project or installed plugin cache. No case authorizes installation, publishing, external messages, Git changes, or network access.

## What a run measures

| Track | Executor receives | What to assess |
| --- | --- | --- |
| `selection` | The real host catalog and discovery controls, fixture, runner constraints, and task messages. | Whether ordinary task wording leads to useful skill selection and proportionate work. Do not name a target skill or preload its instructions to help the executor. |
| `invocation` | The same environment, with the explicit skill request in the task. | Whether the host's manual invocation path works and preserves the requested mode. This is separate from natural selection. |
| `application` | The fixture, runner constraints, task messages, and the specified local skill instructions. | Whether the loaded instructions are followed. Supplying these instructions does not test host discovery or selection. |

The negative discussion case treats setup, cleanup, and handoff as subjects for an explanation. The small-edit case checks that the guide is optional while allowing useful guidance to be read.

## Replay one case

1. Choose a case and the local skill snapshot to evaluate. Record its commit and any uncommitted diff, or hashes of the skill and supporting files. Do not assume an installed cache matches the checkout.
2. Inspect the host's actual capabilities, permission controls, catalog, and invocation rules. Start a fresh executor context with only the case fixture and applicable instructions. For application cases, read the exact files listed in `runner.load_skills`; provide any supporting files needed by those instructions. For selection and invocation cases, expose the actual catalog without adding instructions or a hint about the expected skill. Record any host instruction that already loads a skill.
3. Copy the selected fixture's `files` into a new scratch workspace with the exact relative paths and contents. Keep the evaluator's rubric, the full catalog, and other cases outside the executor's accessible workspace. Do not copy this repository's root `AGENTS.md` into the fixture. Host and safety instructions still apply.
4. Enforce the action restrictions in `default_limits` (network access, external actions, installation, and Git mutations) together with `runner.constraints`, using available host policy or explicit runner instructions. Record which mechanism was used and which capabilities actually exist. Do not invent tools or enable a disabled capability. For a restricted-catalog case, make only the named skills discoverable without altering installed plugins; if isolation is unavailable, mark that condition unexercised.
5. Give the executor only the default action restrictions, case constraints, fixture access, required application instructions, and `task.messages` in order. The task messages are the user task; setup instructions are not part of that wording. The rest of `runner` configures the evaluator's setup and may identify a skill needed for a check; do not paste that metadata into the executor prompt. Do not supply `grader`, expected selections, or likely findings. A runner may extract the allowed fields manually; no special runner is required.
6. Observe the run within `default_limits`, or a case's narrower limits. Stop on completion, a limit, a permission denial, or a needed capability that is unavailable. Use the host's real stop controls; do not start work you cannot manage. Record the stopping reason. A deliberate prohibition in a case is a condition to honor, not a missing capability.
7. Preserve the original and resulting fixture, the response, actual loaded instructions, and available tool or execution trace. Grade separately after the run. Use a separate evaluator context when available and permitted; otherwise label the assessment as self-review. The grader receives the rubric and evidence, not an assumed successful outcome.

Default bounds are five minutes and eight assistant turns per case. Use the host's turn-count definition when available, record it, and enforce the wall-clock bound when a turn cap is unavailable. Running fewer cases is fine; identify the cases actually exercised. Do not repeatedly probe a blocked case or add workers to overcome its constraints.

## Grading and records

Each case has explicit checks and suggested evidence. Mark each check `pass`, `fail`, `blocked`, or `not_exercised`:

- **Pass:** The required observable result is supported by the captured evidence.
- **Fail:** Evidence shows the contract was violated or a required outcome was missed despite the means to exercise it.
- **Blocked:** A needed host capability, permission, or input prevented the check. A tool denial is evidence of a boundary, not evidence that the task succeeded.
- **Not exercised:** The run or available trace did not expose the behavior. For example, a final answer alone cannot establish which skill was loaded or whether a prohibited worker was started.

A case passes only when all its checks pass. Preserve a visible violation even if another check is blocked; report mixed results per check rather than hiding a failure in a case-level success. Reaching a run limit without an observed violation is incomplete, not a pass. State important limitations such as a synthetic source snapshot, unavailable runtime, inherited context, or missing tool visibility.

Keep a run record outside the source tree unless there is a deliberate reason to retain it. A plain text or JSON record is enough. Include:

- Case ID, track, timestamp, fixture identity, and scenario or prompt deviations.
- Skill snapshot and supporting-file hashes or diff; the actual catalog, invocation controls, and instructions loaded, including inherited project or host instructions.
- Host and model names and versions or build identifiers when exposed; relevant settings and whether a value was unknown. Do not infer a model version from a product name.
- Available capabilities, actual permissions, enforcement mechanism, and resource limits.
- Input task messages, output artifacts, tool observations or trace, completion or stopping reason, and evaluator identity or self-review status.
- Each check's result, supporting evidence, meaningful limits, and overall outcome.

Do not include secrets in records. Record what was actually observed; do not fabricate a successful runtime, independent review, or model performance measurement.

## Comparing changes

For a contract check, the instructed run alone is useful. When measuring incremental benefit, an optional control can use the same fixture and task without Anything instructions, in a fresh context. Record any unavoidable difference in host instructions or catalog; a control that inherits the same skill is not a no-skill control.

Compare meaningful cases across multiple fresh runs under the same host, model, permissions, settings, and limits. Report counts and concrete failures along with the setup. A single successful synthetic case supports that observation; it does not establish a success rate, causal improvement, cross-host compatibility, or native routing behavior. Keep selection, invocation, and application results distinct.
