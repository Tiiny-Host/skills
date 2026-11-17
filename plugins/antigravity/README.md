# Tiiny Host plugin for Antigravity

Adds Tiiny Host to Antigravity, Google's coding agent: the Antigravity CLI, which replaces Gemini CLI for most users, and the Antigravity app and IDE. It points Antigravity at the Tiiny Host MCP server to publish, list, update and delete the user's sites, and its skill tells Antigravity to ask before it publishes, replaces or deletes anything.

**Not tested in Antigravity yet.** The folder passes `agy plugin validate --strict`; signing in and publishing from Antigravity haven't been tried.

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
| `skills/tiiny-host/SKILL.md` | How Antigravity should publish: confirm first, one site at a time |
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
