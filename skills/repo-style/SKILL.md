---
name: repo-style
license: Apache-2.0
description: Keep project structure and documentation clear, discoverable, and proportional to the work. Use when adding or organizing files, establishing repository conventions, or updating documentation for software, research, writing, and other projects. Prefer existing conventions and make structural changes only when they solve a concrete problem.
---

# Repository and documentation style

Follow the project's existing organization and the user's requested outcome. Use the defaults below for choices they leave open. A project need not contain code, Git, or a particular toolchain.

## Inspect before organizing

Find the existing entry points, instruction files, source material, outputs, and documentation. Understand how people use them before adding another convention.

Preserve established names and structure when they work. Do not introduce a new architecture, directory taxonomy, build tool, or dependency just because this skill was loaded.

## Structure defaults

- Give important material an obvious home and a descriptive name.
- Use the root README as a concise entry point when the project needs one: purpose, how to use the work, and where to go next.
- Group implementation, source material, tests, assets, and generated results according to the project's language or domain. Do not impose `src/`, `tests/`, or any other directory on every project.
- Add `docs/` or topic directories when the material needs them. Keep a small project small.
- Keep transient output distinct from durable source where useful, following the project's tracking and retention policy.
- Maintain one authoritative explanation of each rule or decision. Link from other places instead of copying it.

When no file operations are available, describe the intended structure or return the proposed content without claiming to have changed it.

## Documentation defaults

Write for the intended reader in plain language. Lead with the purpose or action, then add the context needed to use it.

- Prefer short, concrete explanations and examples that match the real project.
- Use headings, lists, and tables when they make information easier to find or compare.
- Keep quick-start instructions focused on the usual path. Move substantial reference detail to a linked page when needed.
- Document behavior, supported usage, and consequential trade-offs. Include internal mechanics only when they help the reader act.
- Verify commands, paths, and factual claims against accessible source material. Label unverified examples and placeholders.
- Update affected existing documentation when behavior changes. Remove stale instructions instead of adding a competing explanation.
- Create a plan, decision record, changelog entry, or guide when requested or useful to its readers. Do not generate a set of ceremonial documents for every task.

Keep sensitive material out of public documentation. Use the project's normal configuration and secret-handling conventions.

## Project preferences and verification

Use applicable project instructions, including `AGENTS.md` when available. Durable workflow choices belong in the existing instruction or policy location.

If preferences are absent, continue with these defaults. Do not invoke setup automatically or create a new instruction policy as an incidental formatting change. A user can explicitly request setup to establish or update those choices.

Check the affected links, examples, structure, and relevant documentation tooling when available. Match verification to the change; a small wording edit does not require a new test suite. Report the actual result and any meaningful uncertainty.
