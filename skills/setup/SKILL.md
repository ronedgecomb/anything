---
name: setup
license: Apache-2.0
description: Initialize or update a project's workflow preferences in its root AGENTS.md. Use only when the user explicitly requests setup or project instruction configuration. Never select this skill automatically for ordinary work.
disable-model-invocation: true
---

# Setup

Configure the project only after an explicit user request. Discussing, implementing, or reviewing this skill does not invoke it. If it was loaded without a setup request, return to the user's task without changing instructions or starting an interview.

Setup is optional. The other skills provide defaults without it.

## Learn the project

1. Identify the target directory from the request or current context. Clarify it only if ambiguous.
2. Read existing project instructions and relevant documentation when accessible. Inspect enough of the directory to understand its purpose, organization, and known commands. The directory need not contain code or Git.
3. Separate observed facts, explicit preferences, and open choices. Follow existing conventions unless the user wants to change them.
4. Check current capabilities and permissions only as needed to carry out setup. Do not save today's tool availability as a permanent project constraint.

When files are inaccessible, use the context the user supplies and return a proposed instruction file as text. State what you could not inspect.

## Resolve preferences

Use the interview skill if available, or ask directly. Ask only about choices whose answers materially affect future work. Use short rounds, recommendations with reasons, and more discovery when the topic needs it. Do not require answers to a fixed questionnaire.

Consider the applicable choices:

- The project's purpose, typical tasks, and what a good result looks like.
- How much clarification and planning different tasks need, and where durable task records belong.
- Whether delegation is welcome, its resource limits, and any requirement for independent review.
- Appropriate verification and documentation for the work.
- Existing Git message, branch, and integration conventions when Git is used.
- Actions the user wants to retain control over, within the environment's permission limits.

Use lightweight defaults where no preference is stated: proportionate planning and checks, consequential questions, useful and permitted delegation with direct execution as a fallback, concise documentation, and Conventional Commits when Git has no other convention. Existing authorization applies within its scope; new or unclear scope needs clarification.

## Record the result

Start from [assets/agents-template.md](assets/agents-template.md), keeping only applicable sections. Fill or remove every placeholder. The result should be short and useful without the anything plugin installed.

- Create the root `AGENTS.md` when absent and local instruction edits are authorized.
- Preserve existing instructions, comments, and unrelated content. Reuse existing sections where sensible.
- If an anything-managed block exists, update only that block. Otherwise add a small `<!-- anything:start -->` / `<!-- anything:end -->` block for missing preferences. Do not duplicate or contradict existing policy.
- If markers are malformed or repeated, preserve the file and clarify the intended edit instead of guessing a replacement range.
- Resolve material conflicts with the user; keep settled instructions while a choice remains open.
- Record known facts and chosen preferences. Omit unverified commands, secrets, temporary permissions, absolute machine paths, and a snapshot of available workers.
- Summarize useful behavior instead of requiring future agents to have particular sibling skills installed.

An explicit setup request can already authorize these local edits. Do not add a separate approval round unless an unresolved choice or applicable rule requires it. Setup does not authorize repository restructuring, tool installation, Git initialization, or external actions.

## Verify and report

Read the result back. Check that unrelated content is intact, links and documented commands have a source, and no placeholders or conflicting rules remain. Report what changed and any unresolved choice.

Instruction-file discovery varies by host and version. Do not assume that writing `AGENTS.md` makes it active everywhere, or silently replace another entry point. Explain a known discovery issue and the smallest documented way to load the shared instructions. If writing is unavailable, provide the draft and clearly state that it was not saved.
