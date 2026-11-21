# Installation

Install from [ronedgecomb/anything](https://github.com/ronedgecomb/anything) using a native package or select individual skills. Installation configures your chosen agent; skills do not run these commands automatically.

## Antigravity plugin

```sh
agy plugin install https://github.com/ronedgecomb/anything
```

The Antigravity CLI, app, and IDE share this global installation. Run `agy plugin list` to confirm that `anything` is enabled. [Antigravity plugin documentation](https://antigravity.google/docs/plugins)

## Claude Code plugin

In Claude Code:

```text
/plugin install anything --marketplace ronedgecomb/anything
```

You can also add the marketplace explicitly:

```text
/plugin marketplace add ronedgecomb/anything
/plugin install anything@anything-marketplace
```

Skills are namespaced, for example `/anything:setup`, `/anything:cleanup`, `/anything:handoff`, and `/anything:interview`.

## Codex plugin

```sh
codex plugin marketplace add ronedgecomb/anything
codex plugin add anything@anything-marketplace
```

Use the installed host's skill selector to explicitly invoke setup, cleanup, or handoff. With standalone installations, use `$setup`, `$cleanup`, or `$handoff`.

## Pi package

```sh
pi install git:github.com/ronedgecomb/anything
```

Use `/skill:setup`, `/skill:cleanup`, `/skill:handoff`, or `/skill:interview` to invoke a skill explicitly.

## Individual skills, including OpenCode

```sh
npx skills add ronedgecomb/anything
```

Choose the agents and skills you want. The installer uses project scope by default; add `-g` for user scope across projects. To select targets explicitly:

```sh
npx skills add ronedgecomb/anything --agent codex claude-code opencode pi
```

Installers require their own runtime; the instruction-only skills do not. You can also copy a complete `skills/<name>/` folder, including its license and notice, into a discovery directory supported by your agent.

OpenCode 2 can load setup, cleanup, or handoff explicitly with `@setup`, `@cleanup`, or `@handoff`. Check invocation controls before installing a manual-only skill into an automatically discovered directory. [Compatibility](compatibility.md#manual-only-skills)

## Develop from a checkout

Clone the repository and run the relevant commands from its root:

```sh
git clone https://github.com/ronedgecomb/anything.git
cd anything
```

For Antigravity, install the current directory as a plugin.

```sh
agy plugin install .
```

For a Claude Code development session:

```sh
claude --plugin-dir .
```

For a local Codex marketplace:

```sh
codex plugin marketplace add .
codex plugin add anything@anything-marketplace
```

For a local Pi package:

```sh
pi install ./
```

For individual skills from the checkout:

```sh
npx skills add ./
```

Installers may use cached or copied content. Reload or reinstall as required by the host when testing changes.

## Release versioning

Keep the version in `plugin.json`, `.claude-plugin/plugin.json`, and `package.json` identical. Bump it whenever skill instructions, bundled supporting files, or plugin behavior or packaging change. Use a patch for corrections, a minor for new skills or compatible capabilities, and a major for breaking changes. Related edits shipped together share one bump; repository-only documentation changes do not require one.

Claude Code caches marketplace-installed plugin content by version. Changing the repository while keeping the same manifest version can leave users on older files even after an update. A new release version makes the changed content eligible for installation; users still need to update and reload it. See [Claude Code versioning](https://code.claude.com/docs/en/plugins/manifest-reference#version).

If changes have already been merged without a bump, release the current content under one new version. That release includes the accumulated changes; earlier commits do not need rewriting or separate retroactive version bumps.

## Configure a project

Ordinary tasks can use the skills immediately. Explicitly invoke setup only when you want to initialize or update project instructions.

Check which instruction file your installed host loads, particularly when `AGENTS.md` and an existing host-specific instruction file coexist. Follow that host's documented settings or import mechanism if needed; avoid maintaining duplicate copies of the same project policy.
