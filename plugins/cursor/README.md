# Tiiny Host plugin for Cursor

Adds Tiiny Host to Cursor, the AI code editor. It points Cursor's agent at the Tiiny Host MCP server to publish, list, update and delete the user's sites.

**Not tested in Cursor yet.** The plugin loads in Cursor with its skill (Nov 10, 2026); signing in and publishing from Cursor haven't been tried.

## Install

Once Cursor lists it: open the Cursor Marketplace, search "Tiiny Host" and install.

## What it contains

| File | Purpose |
|---|---|
| `.cursor-plugin/plugin.json` | The plugin's name, description, author and logo |
| `mcp.json` | The address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Cursor's agent |
| `assets/logo.png` | The Tiiny Host icon shown in the Marketplace |

`.cursor-plugin/marketplace.json` at the root of this repository points Cursor to this folder.

## Network and credentials

The plugin runs no code and no hooks on the user's machine. It connects only to `https://mcp.tiiny.host/oauth`, with the user's own Tiiny Host sign-in. It asks for no keys and reads no files or environment variables.

## How it gets listed

Cursor reviews every plugin by hand. Submit the link to this public repository at https://cursor.com/marketplace/publish.

To try it before it is listed, copy this folder to `~/.cursor/plugins/local/tiiny-host` and run **Developer: Reload Window** in Cursor.

Cursor's rules: https://cursor.com/docs/reference/plugins
