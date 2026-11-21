# Axad plugins

Axad is an AI language tutor. This folder is the Axad plugin for the agents that show Axad's widgets, with their taps: **Claude** (web, desktop and mobile), **ChatGPT**, and **Codex in the ChatGPT desktop app**. Each bundles:

- the remote MCP server `https://mcp.axad.ai/mcp` (OAuth 2.1; many tools work before you sign in),
- Axad's teaching skills (`axad-tutor`, `axad-inburgering`).

In these hosts Axad answers as its own app does: one stack of cards per reply (the `show_cards` tool), some open, a few folded, with next-step buttons, and a popup on selected text.

A host that shows no views (a terminal agent such as Claude Code or the Codex CLI) is not a supported Axad platform.

`plugins/` is published as its own public repository, `axad-ai/plugins`. The MCP server alone also works without a plugin: see [axad.ai/developers](https://axad.ai/developers).

## Install

Claude (web and desktop; a connector added there also shows on mobile): Customize → Plugins → Add → Add marketplace, and paste `axad-ai/plugins`'s Git URL.

Codex in the ChatGPT desktop app: add the marketplace `axad-ai/plugins` in Plugins, choose Axad, and install.

ChatGPT on the web: Plugins → Add custom MCP server → `https://mcp.axad.ai/mcp`.

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
