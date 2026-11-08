# Defaults and project preferences

Anything provides defaults through focused skills. Setup is optional, and each skill includes enough guidance to work independently.

## Precedence

Follow the user's instructions and the environment's restrictions. Within those limits, explicit task decisions and applicable project instructions take precedence over anything's defaults. Resolve material ambiguity with the user; preserve decisions that are already clear.

A skill, project file, or installed tool cannot grant permission that the current environment withholds.

## Default choices

| Area | Default |
| --- | --- |
| Understanding | Inspect available context before asking for facts. Ask about consequential unknowns. |
| Interviews | Use short rounds and adapt their depth to the topic. Recommendations should explain their trade-offs. |
| Planning | Use the smallest plan that makes the task clear. Persist one when continuity or complexity benefits. |
| Delegation | Use it only when useful, available, and permitted. Direct sequential work is a complete execution mode. |
| Implementation | Prefer the smallest clear, complete change that follows project conventions. Add complexity when it solves a concrete problem. |
| Review | Prefer a separate context when useful and available. Label self-review and unverified claims honestly. |
| Verification | Use existing checks where they suffice. Add or update tests for meaningful failures or required behavior. Report actual checks and limits. |
| Completion | Finish when the requested outcome is complete and applicable checks pass. Continue necessary work within authorization; ask before pursuing unrelated findings, or defer them. |
| Cleanup sweeps | Explicit invocation only. Fix clear issues that preserve behavior within the requested scope; discuss larger changes. Honor findings-only requests. |
| Follow-ups | Report the issue, evidence or location, and next step. Ask before adding it to an existing tracker or `TODO.md` unless already authorized; otherwise use the conversation without creating a tracker. |
| Authorization | Continue within existing authorization. Ask before crossing its scope or a required approval boundary. |
| Git | Prefer Conventional Commits when the project has no established message convention. Follow its branch and integration rules. |
| Structure | Keep the existing project shape unless changing it solves a concrete problem. |
| Documentation | Maintain concise entry points and durable decisions close to their subject. Add documents when they have a reader and a purpose. |

These defaults do not require Git, subagents, a particular shell, a task directory, a pull request, a security reviewer, or a deployment step.

## What setup records

Keep the project purpose, known commands, workflow preferences, repository conventions, review expectations, and relevant boundaries in the project's root `AGENTS.md`. Include only applicable, settled choices.

Merge with existing instructions. Keep the file useful even if the anything skills are later unavailable: summarize the chosen behavior rather than relying on a list of skill names.

Do not persist today's agent count, installed tool list, authentication state, absolute machine paths, or temporary permission decisions as permanent project facts. Re-evaluate capabilities in each session.

## Composition

Use another skill when it is installed and helps. Otherwise apply the current skill directly. Resolve supporting files relative to the directory containing that skill's `SKILL.md`.

Cleanup provides an explicitly requested repository sweep using these defaults. Its relevant areas and findings are within that requested scope; ordinary tasks still defer unrelated cleanup. See [repository cleanup](cleanup.md) for coverage and optional skill composition.

Some work ends with a conversation or a draft; other work ends with a tested change or a published artifact. Carry out only the stages needed for the requested outcome.
