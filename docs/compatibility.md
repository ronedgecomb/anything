# Compatibility

Behavioral instructions are based on capabilities and permissions, not product names. Host-specific installation and invocation details belong in metadata or documentation.

The following invocation behavior is documented by the hosts. It is not a claim that complete sessions have been tested in every host and version.

## Manual setup

| Host | Selection control |
| --- | --- |
| Codex | `skills/setup/agents/openai.yaml` sets `policy.allow_implicit_invocation: false`. |
| Claude Code | Setup's `disable-model-invocation: true` frontmatter disables automatic invocation. |
| Pi | The same frontmatter hides setup from automatic model selection; explicit skill invocation remains available. |
| OpenCode 2 | The same frontmatter omits setup from the model's available list; explicit `@setup` loading remains available. |
| Older or other hosts | Verify their invocation controls. The setup body also requires an explicit user request before any configuration work. |

OpenCode 1 ignores unknown frontmatter and does not provide the same automatic-selection control. For strict manual-only use on such a host, leave setup out of discovered skill directories when installing the other skills. Keep a checkout elsewhere and explicitly supply its `skills/setup/SKILL.md` only when requesting setup.

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
| Delegation available but prohibited | Direct execution; no native workers or subprocess workaround. |
| Only permitted subprocess workers available | Check tooling and lifecycle controls, pass a bounded brief, collect actual results. |
| No workers, Git, or writable files | Work sequentially and return the requested content; do not fabricate commits or saved artifacts. |
| Review without a separate context | Useful self-review with an accurate independence statement. |
| An interview without a question tool | Adaptive questions in normal conversation. |
| Only one skill installed | Complete its task without requiring sibling skills or root repository resources. |
| A user has already authorized the action | Continue within that scope; ask again only for a material change or another required boundary. |
| Setup with existing instructions | Preserve unrelated content, resolve conflicts, and update only settled preferences. |
| Setup with limited discovery | Omit unknown commands and unsupported claims rather than inventing them. |
