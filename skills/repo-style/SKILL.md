---
name: repo-style
license: Apache-2.0
description: Keep project structure and documentation clear, discoverable, and proportional to the work. Use when adding or organizing files, establishing repository conventions, or writing and updating documentation for software, research, writing, and other projects. Prefer existing conventions and make structural changes only when they solve a concrete problem.
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

Write for the intended reader's ongoing need, not the author's recent task. Lead with the purpose or action, then add only the context needed to use it.

- Prefer short, concrete explanations and examples that match the real project. Cut throat-clearing, promotional framing, redundant restatements, and obvious filler.
- Size detail to the document's role, not the effort spent on the current change. Keep quick-start instructions and READMEs focused on the usual path; move substantial reference detail or edge cases to a linked page when needed.
- Use headings, lists, and tables when they make information easier to find or compare.
- Document current behavior, supported usage, and consequential trade-offs. Include internal mechanics only when they help the reader act.
- Put task narrative and fix rationale in commit messages, change summaries, or decision records rather than durable prose, unless the reader needs an ongoing constraint or migration step.
- When user-facing behavior changes, revise or replace affected wording in place so existing sections stay cohesive and proportionate. Avoid bolting on new paragraphs, callouts, or defensive caveats for narrow fixes, and leave top-level docs unchanged when an internal fix only preserves already-documented behavior.
- Verify commands, paths, and factual claims against accessible source material. Label unverified examples and placeholders.
- Create a plan, decision record, changelog entry, or guide when requested or useful to its readers. Do not generate a set of ceremonial documents for every task.

Before keeping an added sentence or section, check what the reader would get wrong without it. If it only restates earlier text, narrates the recent edit, or explains obvious behavior, omit it.

| Situation | Useful result |
| --- | --- |
| An internal bugfix aligns code with existing behavior | Explain the fix in the commit message or summary; leave the README unchanged. |
| A change alters a supported option or default | Update the affected line or section in place instead of appending a "now/no longer" paragraph. |
| A narrow edge case matters only to operators or maintainers | Put it in linked reference docs or a concise comment where it applies, not the root README. |
| Revising an over-explained section | Remove filler and repetition while keeping real constraints, numbers, commands, and caveats intact. |

When revising factual or technical prose, identify the details that must survive: names, numbers and units, commands, paths, links, conditions, trade-offs, established terminology, and uncertainty. Compare the edited text with the original and its sources. Preserve those details or explain factual corrections supported by evidence; clearer wording must preserve the claim's scope and necessary qualifiers. Match the depth of this check to the risk of changing the meaning; a separate inventory or report is optional.

Keep sensitive material out of public documentation. Use the project's normal configuration and secret-handling conventions.

## Project preferences and verification

Use applicable project instructions, including `AGENTS.md` when available. Durable workflow choices belong in the existing instruction or policy location.

If preferences are absent, continue with these defaults. Do not invoke setup automatically or create a new instruction policy as an incidental formatting change. A user can explicitly request setup to establish or update those choices.

Check the affected links, examples, structure, and relevant documentation tooling when available. Match verification to the change; a small wording edit does not require a new test suite. Report the actual result and any meaningful uncertainty.
