# Compatibility

Behavioral instructions are based on capabilities and permissions, not product names. Host-specific installation and invocation details belong in metadata or documentation.

The following invocation behavior is documented by the hosts. It is not a claim that complete sessions have been tested in every host and version.

## Manual setup and cleanup

| Host | Selection control |
| --- | --- |
| Codex | Each skill's `agents/openai.yaml` sets `policy.allow_implicit_invocation: false`. |
| Claude Code | Both skills' `disable-model-invocation: true` frontmatter disables automatic invocation. |
| Pi | The same frontmatter hides both skills from automatic model selection; explicit skill invocation remains available. |
| OpenCode 2 | The same frontmatter omits both skills from the model's available list; explicit `@setup` or `@cleanup` loading remains available. |
| Older or other hosts | Verify their invocation controls. Each skill's body also requires an explicit user request before starting its work. |

OpenCode 1 ignores unknown frontmatter and does not provide the same automatic-selection control. For strict manual-only use on such a host, leave setup and cleanup out of discovered skill directories when installing the other skills. Keep a checkout elsewhere and explicitly supply the relevant `skills/<name>/SKILL.md` only when requesting that skill.

Invocation controls govern skill selection. They are not an execution sandbox, and project preferences never override the host's permissions.

References: [Codex invocation policy](https://learn.chatgpt.com/docs/build-skills#optional-metadata), [Claude Code invocation control](https://code.claude.com/docs/en/skills#control-who-invokes-a-skill), [Pi skills](https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/skills.md), [OpenCode 2 frontmatter](https://opencode.ai/docs/skills/#frontmatter), [OpenCode 1 frontmatter](https://opencode.ai/v1/docs/skills/#write-frontmatter).

## Runtime choices

- Use native delegation when it is available, permitted, and worthwhile.
- Use subprocess workers only when suitable agent tooling is already available and authorized, and you can track completion, collect results, and stop the processes you start.
- Never route through subprocesses to evade a restriction on delegation.
- Without delegation, perform the task directly. Without parallelism, sequence the work.
- Without a shared filesystem, pass a self-contained brief or snapshot. Do not assume another worker can read a local absolute path.
- Without writable files, return the intended artifact as text and state that it was not saved.
- Without Git, omit branches, commits, worktrees, and pull requests.
- Without a question interface, ask in ordinary conversation. Respect the actual interface's limits when one is available.
- Without a separate context, label a review as self-review. If independence is required, provide a handoff brief and state that independent review remains outstanding.
- Do not invent tools, APIs, model controls, persistent memory, or process-management capabilities. Recheck what the current session actually provides.

## Project instruction discovery

Setup uses `AGENTS.md` as the canonical project artifact. Whether it is automatically loaded depends on the installed host, version, settings, and other instruction files.

For example, current [Claude Code instructions](https://code.claude.com/docs/en/memory#agentsmd) describe conditional AGENTS.md loading when other project instruction files are present. Use the host's documented configuration or an explicit import when necessary, preserving existing instructions.

## Behavioral checks

Exercise these cases when changing a skill or claiming support for another host:

| Situation | Expected behavior |
| --- | --- |
| A small task with no setup | Useful work with proportionate checks; no setup interview or mandatory plan file. |
| A small text or presentation change | A focused edit with applicable existing checks or direct inspection; add automated coverage when behavior or project requirements justify it. |
| A one-line behavior fix with a regression gap | A clear, complete fix and a focused regression test when needed; patch size alone does not determine verification. |
| Tests tied to incidental implementation details | Prefer stable checks of required behavior; retain implementation-specific assertions when those details are part of the required contract. |
| Requested work complete and applicable checks pass | Finish and report deferred findings; do not extend the task for unrelated improvements. |
| An unrelated defect or cleanup opportunity appears during work or review | Ask before further investigation, fixes, or delegation, or defer it with available evidence and a next step. |
| A newly discovered issue blocks the requested outcome | Resolve it within existing authorization; ask if resolving it exceeds that scope. |
| An existing tracker or `TODO.md` could hold a follow-up | Ask before adding it unless the user or project instructions already authorize recording it there. Its existence alone is not permission. |
| No established follow-up destination | Report the issue, evidence or location, and next step in the conversation for a future session; do not create a tracking system or start the work. |
| Delegation available but prohibited | Direct execution; no native workers or subprocess workaround. |
| Only permitted subprocess workers available | Check tooling and lifecycle controls, pass a bounded brief, collect actual results. |
| No workers, Git, or writable files | Work sequentially and return the requested content; do not fabricate commits or saved artifacts. |
| Review without a separate context | Useful self-review with an accurate independence statement. |
| An interview without a question tool | Adaptive questions in normal conversation. |
| Only one skill installed | Complete its task without requiring sibling skills or root repository resources. |
| A user has already authorized the action | Continue within that scope; ask again only for a material change or another required boundary. |
| Skill content or plugin behavior changes for a release | Bump the version consistently across all three manifests; related changes in one release share a bump. |
| A new skill is missing after an installed Claude plugin is updated | Check the installed components, manifest version, project scope, and enabled state. Refresh the marketplace, update the plugin, and reload or restart the session; do not assume the checkout and installed cache match. |
| Setup with existing instructions | Preserve unrelated content, resolve conflicts, and update only settled preferences. |
| Setup with limited discovery | Omit unknown commands and unsupported claims rather than inventing them. |
| Authoring or discussing cleanup, or doing an ordinary implementation task | Do not start a cleanup sweep without an explicit request. |
| Cleanup with no additional mode specified | Inspect the requested scope, fix clear issues that preserve behavior, and discuss larger changes; reuse existing authorization. |
| Cleanup requested as findings only | Inspect without changing repository files, including through checks with write effects; return prioritized evidence and next steps. |
| Cleanup limited to named areas or concerns | Respect the requested boundaries and resource limits; report inspected, sampled, and skipped areas honestly. |
| Cleanup finds similar independently installed components, fixtures, or license files | Preserve intentional duplication and required attribution; consolidate only when semantics and boundaries support it. |
| Cleanup finds material with no search references | Check dynamic, exported, configured, packaged, and compatibility consumers before proposing removal; do not assume it is unused. |
| Cleanup uses workers with overlapping findings or shared files | Verify and merge findings by root cause; establish ownership and sequence conflicting writes or checks. |
| Cleanup encounters existing edits or untracked files | Preserve unrelated work and user data; do not treat repository status as a removal list. |
| Cleanup identifies a suspected performance problem | Distinguish hypotheses from demonstrated costs and measured improvements. |
| Cleanup has no actionable findings after a bounded pass | Report coverage and checks, then finish without inventing findings or requiring repeated sweeps. |
