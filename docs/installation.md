# Installation

Install from [ronedgecomb/anything](https://github.com/ronedgecomb/anything) using a native package or select individual skills. Installation configures your chosen agent; skills do not run these commands automatically.

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

Skills are namespaced, for example `/anything:setup`, `/anything:cleanup`, and `/anything:interview`.

## Codex plugin

```sh
codex plugin marketplace add ronedgecomb/anything
codex plugin add anything@anything-marketplace
```

Use the installed host's skill selector to explicitly invoke setup or cleanup; standalone installations use `$setup` or `$cleanup`.

## Pi package

```sh
pi install git:github.com/ronedgecomb/anything
```

Use `/skill:setup`, `/skill:cleanup`, or `/skill:interview` to invoke a skill explicitly.

## Individual skills, including OpenCode

```sh
npx skills add ronedgecomb/anything
```

Choose the agents and skills you want. The installer uses project scope by default; add `-g` for user scope across projects. To select targets explicitly:

```sh
npx skills add ronedgecomb/anything --agent codex claude-code opencode pi
```

Installers require their own runtime; the instruction-only skills do not. You can also copy a complete `skills/<name>/` folder, including its license and notice, into a discovery directory supported by your agent.

Current OpenCode 2 can load setup or cleanup explicitly with `@setup` or `@cleanup`. Older hosts may ignore invocation controls: consult [compatibility](compatibility.md) before installing either skill into an automatically discovered directory.

## Develop from a checkout

Clone the repository and run the relevant commands from its root:

```sh
git clone https://github.com/ronedgecomb/anything.git
cd anything
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

## Configure a project

Ordinary tasks can use the skills immediately. Explicitly invoke setup only when you want to initialize or update project instructions.

Check which instruction file your installed host loads, particularly when `AGENTS.md` and an existing host-specific instruction file coexist. Follow that host's documented settings or import mechanism if needed; avoid maintaining duplicate copies of the same project policy.
