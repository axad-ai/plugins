# Axad plugins

Axad is an AI language tutor. This folder is the Axad plugin for **Claude** (Claude Code, Claude Desktop, Cowork) and for **ChatGPT and Codex**. Each bundles:

- the remote MCP server `https://mcp.axad.ai/mcp` (OAuth 2.1; many tools work before you sign in),
- Axad's teaching skills (`axad-tutor`, `axad-inburgering`).

`plugins/` is published as its own public repository, `axad-ai/plugins`. The MCP server alone also works without a plugin: see [axad.ai/developers](https://axad.ai/developers).

## Install

Claude Code:

```
/plugin marketplace add axad-ai/plugins
/plugin install axad@axad
```

Claude Desktop and Cowork: Customize → Plugins → Add → Add marketplace, and paste `axad-ai/plugins`'s Git URL.

Codex (CLI or the ChatGPT desktop app):

```
codex plugin marketplace add axad-ai/plugins
```

then open `/plugins`, choose Axad, and install. ChatGPT on the web: Plugins → Add custom MCP server → `https://mcp.axad.ai/mcp`.

The first call of a tool that needs your account asks you to sign in once.

## Layout

```
.claude-plugin/marketplace.json     Claude's marketplace
.agents/plugins/marketplace.json    Codex's marketplace
axad/                               the plugin, read by both
  .claude-plugin/plugin.json, .mcp.json     Claude's manifest and MCP server
  plugin.json, mcp.json                     the portable Agent Plugins manifest and MCP server (Codex, ChatGPT)
  skills/                                   copied from harness/skills/
  assets/logo.svg
```

Everything here is written by one script from the same sources, and none of it is edited by hand:

```
bun plugins/build.ts           write
bun plugins/build.ts --check   fail when a file is missing, differs or is stale
```

After a change to a skill in `harness/skills/`, run the build and bump `VERSION` in `build.ts`: a host that pinned a version only updates when it changes.
