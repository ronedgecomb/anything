# Working on anything

## Purpose

Anything is a lightweight collection of opinionated, independently useful agent skills for software, research, writing, planning, and other work.

Keep useful defaults available without setup. Setup and cleanup are explicitly user-invoked. Setup records durable project preferences in `AGENTS.md`; it must preserve existing instructions and avoid baking in the current harness or environment.

## Authoring

- Keep behavioral instructions based on capabilities and permissions, not named agent tools. Put host-specific installation and invocation details in metadata or documentation.
- Delegation is optional. Support direct execution, and describe subprocess workers only when tooling and lifecycle controls are available and their use is permitted. Never use a fallback to bypass a restriction.
- Make every skill useful on its own. Keep required templates, references, licenses, and notices inside that skill's directory; sibling skills and root repository resources are optional.
- Match planning, questions, verification, and documentation to the task. Avoid mandatory agent counts, Git operations, approval rituals, or document sets for all work.
- Distinguish observations from assumptions and independent review from self-review. Report actual checks and limitations.
- Respect existing project conventions and authorization within their scope. Ask about consequential unknowns or new scope, not decisions already established.
- Keep changes focused. Maintain existing names and organization unless changing them solves a concrete problem.

## Files and metadata

- Each skill lives in `skills/<name>/SKILL.md`, with a matching lowercase kebab-case frontmatter name and a clear description of when it applies.
- Supporting paths are relative to the skill directory.
- Keep setup and cleanup's manual-invocation frontmatter and their `agents/openai.yaml` policies intact.
- Keep names and versions consistent in `plugin.json`, `.claude-plugin/plugin.json`, and `package.json`. Keep both marketplace catalogs aligned with the plugin identity.
- Bump the shared version whenever skill instructions, bundled supporting files, or plugin behavior or packaging change. Related edits in one release share one bump; repository-only documentation changes do not require one. Use a patch for corrections, a minor for new skills or compatible capabilities, and a major for breaking changes. See [release versioning](docs/installation.md#release-versioning) for the update and cache behavior.
- Use `Apache-2.0` licensing metadata. Keep each skill's `LICENSE.txt` and `NOTICE` identical to the root `LICENSE` and `NOTICE` so individual installations retain the terms and attribution.
- `assets/` holds the wordmark and plugin icon, drawn as outlines in ink `#111111` and paper `#eeeeee`, so no font is required. The README and manifests reference these files; skills must not depend on them. See [logos and icons](docs/compatibility.md#logos-and-icons) for each host's field.
- Use `README.md` for the entry point and `docs/` for substantial installation, defaults, and compatibility detail. Update the relevant documentation when behavior changes. Do not add a repository changelog.
- `CLAUDE.md` imports this file; maintain project instructions here rather than duplicating them.

## Verification

This is an instruction-only repository. There is no required build, runtime dependency installation, or application test suite.

For relevant changes, check JSON and YAML metadata, names and versions, local Markdown links, self-contained skill references, and the affected cases in [docs/compatibility.md](docs/compatibility.md). Check that skill instructions and examples agree.

Run `git diff --check` before committing. When the CLI is available, validate the native Claude manifests:

```sh
claude plugin validate .claude-plugin/plugin.json --json
claude plugin validate .claude-plugin/marketplace.json --strict
```

Expect the plugin validator's warning that root `CLAUDE.md` is not loaded as installed plugin context: it is deliberately for contributors. Check that the report has no errors, and investigate any other manifest or content warnings. Strict mode also rejects that intentional warning.

These validate packaging, not end-to-end agent behavior. Do not claim runtime testing in a host that was not exercised. Keep validation from changing installed plugins as a side effect.

## Git

Use Conventional Commits for normal development, with focused commits and configured author identity. The initial public snapshot intentionally uses `Initial commit`.

Preserve unrelated work. Commit, publish, or rewrite history within the user's authorized scope, respecting applicable restrictions. Do not add a repeated approval step to an action already authorized.
