# Tiiny Host plugin for Antigravity

Adds Tiiny Host to Antigravity, Google's coding agent: the Antigravity CLI, which replaces Gemini CLI for most users, and the Antigravity app and IDE. It points Antigravity at the Tiiny Host MCP server to publish, list, update and delete the user's sites.

Tested in the Antigravity CLI 1.5.10 on Nov 18, 2026, installed with `agy plugin install` from a copy of this folder: it signed in with a Tiiny Host account in the browser, published a page and deleted it. The folder passes `agy plugin validate --strict`. The Antigravity app and IDE haven't been tried.

## Install

Once Google lists it: in the Antigravity CLI run `/plugin`, find "Tiiny Host" on the Discover tab and install it, or run

```bash
agy plugin install tiiny-host
```

## What it contains

| File | Purpose |
|---|---|
| `plugin.json` | The plugin's name, description, logo, starter prompts and author |
| `mcp_config.json` | The address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Antigravity |
| `assets/logo.png` | The Tiiny Host icon shown in the Marketplace |

## Network and credentials

The plugin runs no code and no hooks on the user's machine. It connects only to `https://mcp.tiiny.host/oauth`, with the user's own Tiiny Host sign-in. It asks for no keys and reads no files or environment variables.

## How it gets listed

Google lists plugins in the Antigravity Marketplace after a partner intake form: https://forms.gle/2EX5RFYPoJe1UgxR9. Check the folder before each submission and release, with zero errors and zero warnings:

```bash
agy plugin validate --strict ./plugins/antigravity
```

To try it before it is listed, install it from a clone of this repository:

```bash
agy plugin install ./plugins/antigravity
```

Google's rules: https://antigravity.google/docs/build-plugins
