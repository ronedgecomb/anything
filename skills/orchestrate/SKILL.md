---
name: orchestrate
license: Apache-2.0
description: Coordinate a task with multiple steps, areas, or contributors, including research, writing, implementation, and review. Use when the work benefits from explicit sequencing or delegation. Scale the process to the outcome and available capabilities; a single agent can carry out the whole task.
---

# Orchestrate

Own the requested outcome, integration, evidence, and conversation with the user. Choose a process that fits the task. Follow applicable instructions and authorization; use lightweight defaults for choices they leave open.

## Establish the work

1. Read the available context and identify the outcome, constraints, and meaningful unknowns.
2. Clarify decisions that affect the result. Use an interview skill if installed and useful, or ask directly. Do not invoke setup for an ordinary task.
3. Choose the smallest useful plan. Keep short tasks in the conversation; persist a record when continuity or complexity benefits. A task-plan skill is optional.
4. Select the stages this task needs: investigation, research, drafting or implementation, documentation, review, verification, and delivery. Skip stages that add no value. A task need not involve code, Git, or publication.

## Choose how to execute

Check the relevant capabilities and permissions in the current session. Availability alone is not authorization; do not infer capabilities from the product name or promise tools you do not have.

- Work directly when the task is small, tightly coupled, or cheaper to complete than to hand off.
- Use native subagents when delegation is useful, supported, and permitted.
- If native delegation is unavailable, consider subprocess-based workers only when suitable tooling is already available, permitted, and manageable. You must be able to collect their output, identify completion or failure, and stop the processes you start.
- If delegation is prohibited, do not use subprocesses or another mechanism to bypass that restriction.
- When workers or safe parallelism are unavailable, perform the same relevant stages directly and sequentially. Treat this as a complete way to do the work.

Respect the user's resource limits and the actual controls available for worker count and execution effort. Do not install agent tooling, alter permission settings, or start unmanaged background work to obtain delegation.

## Delegate when it helps

Use [references/brief-template.md](references/brief-template.md) for a self-contained handoff, adapting the role and report to the task.

- Give each worker a bounded outcome, relevant context, constraints, owned artifacts or resources, verification criteria, and a report format.
- Confirm how it will access inputs and return results. Supply relevant content when a local path is inaccessible; do not assume shared memory or a shared filesystem.
- Split independent work. Establish shared decisions or interfaces only when needed, without requiring a preliminary commit.
- Prevent conflicting writes and shared-resource collisions. Use isolation when supported and helpful, or sequence the work. See [references/parallel-work.md](references/parallel-work.md).
- Keep external actions and other restricted work within the authorization assigned to that worker. A handoff cannot expand permission.
- Track actual completion. Resume an existing worker only if supported; otherwise use a new bounded handoff or finish directly.
- If delegation fails, inspect what completed, collect useful partial results, and continue through an available path.

## Integrate and verify

Check important claims against the artifacts or source evidence before reporting them. Resolve contradictions and integration failures. Distinguish facts, assumptions, and recommendations.

Review the result at an appropriate scope. A separate reviewer can help when available and permitted; otherwise make a deliberate self-review and label it accurately. If independent review is an explicit requirement, state when it remains unmet. A fresh-review skill can help but is not required.

Run checks appropriate to the work and the project's rules. After changes, repeat affected checks; run a full suite when required or justified. Report pre-existing or unrelated failures without silently expanding the task to fix everything.

Git branches, worktrees, commits, pull requests, deployment, and cleanup are conditional steps. Follow project conventions and the actual request. Do not make a shipping action part of every task; resolve missing authorization before taking it.

## Communicate and finish

Give concise updates during sustained work: what is known, what completed, and what remains. Do not present a worker's forecast as a result.

Deliver the requested artifact or answer with the evidence needed to assess it. State verification limits and genuine outstanding requirements. Update an existing record when useful; do not require a new document, persistent memory entry, or TODO system for every task.
