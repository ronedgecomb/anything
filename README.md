# anything

Opinionated, lightweight agent skills for pretty much anything.

Start with the skills you need. Setup is optional: useful defaults are included in each skill, and setup records your project's preferences in `AGENTS.md`.

## Defaults

- Match the amount of planning, questioning, verification, and documentation to the task.
- Prefer the smallest clear, complete change. Add complexity when it has a concrete benefit, and tests when they provide meaningful confidence.
- Follow the user's request and existing project conventions. Use anything's defaults for choices they leave open.
- Delegate only when it is useful, available, and permitted. Work directly when it is not.
- Keep decisions and findings grounded in evidence. Distinguish independent review from self-review.
- Respect authorization already given within its scope. Ask when an action needs permission that is missing or unclear.
- Defer unrelated findings. Ask before pursuing them or adding them to an existing tracker unless already authorized; otherwise report them for later.
- Prefer Conventional Commits when Git is used and the project has no other convention.

The skills are instructions loaded when relevant or explicitly invoked; installing the plugin does not replace the host's instructions or grant additional permissions.

## Skills

| Skill | Use it to |
| --- | --- |
| [setup](skills/setup/SKILL.md) | Explicitly initialize or update project preferences in `AGENTS.md`. Manual invocation only. |
| [interview](skills/interview/SKILL.md) | Clarify a topic, goal, decision, or set of requirements through an adaptive conversation. |
| [orchestrate](skills/orchestrate/SKILL.md) | Coordinate work at the right scale, with optional delegation. |
| [task-plan](skills/task-plan/SKILL.md) | Keep a concise plan and handoff record when the task benefits from one. |
| [fresh-review](skills/fresh-review/SKILL.md) | Review an artifact using a separate context when possible, or an explicitly labeled self-review. |
| [approval-gate](skills/approval-gate/SKILL.md) | Resolve authorization for consequential actions without repeating approvals unnecessarily. |
| [git-style](skills/git-style/SKILL.md) | Prepare focused changes and use Conventional Commits by default. |
| [repo-style](skills/repo-style/SKILL.md) | Keep project structure and documentation clear and proportional. |

Each skill works on its own. References to other skills are optional helpers; their installation is not a prerequisite.

## Setup

Explicitly invoke `setup` when you want to configure a project. It reads what is already there, asks only about unresolved choices, and creates or updates a small section of the root `AGENTS.md`. Existing instructions are preserved. Without file access it returns a draft instead.

Project preferences persist; tool availability and permissions are checked in the current session. Ordinary tasks do not trigger setup.

## Installation

### Claude Code

```text
/plugin install anything --marketplace ronedgecomb/anything
```

### Codex

```sh
codex plugin marketplace add ronedgecomb/anything
codex plugin add anything@anything-marketplace
```

### Pi

```sh
pi install git:github.com/ronedgecomb/anything
```

### Individual skills, including OpenCode

```sh
npx skills add ronedgecomb/anything
```

Choose the skills and agents you want. See [installation](docs/installation.md) for local development, [defaults](docs/defaults.md) for project preferences, and [compatibility](docs/compatibility.md) for version-specific details. No runtime dependencies are required by the instruction-only skills themselves.

## Layout

- `skills/<name>/SKILL.md`: portable behavioral instructions.
- Skill-local `references/` and `assets/`: optional briefs, examples, and templates.
- `plugin.json` and `.claude-plugin/plugin.json`: plugin manifests.
- `.agents/plugins/marketplace.json` and `.claude-plugin/marketplace.json`: installation catalogs.
- `package.json`: Pi package metadata.

## Contributing

Read [AGENTS.md](AGENTS.md) for repository conventions and verification guidance. `CLAUDE.md` imports the same instructions. These files guide work on this repository; installed skills do not inject them into your project.

## License

Copyright 2026 Ron Edgecomb. Licensed under the [Apache License, Version 2.0](LICENSE). Each skill bundles its license and attribution for individual installation.
