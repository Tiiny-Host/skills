# Tiiny Host plugin for Grok Build

Adds Tiiny Host to Grok Build, xAI's coding agent for the terminal. It points Grok at the Tiiny Host MCP server to publish, list, update and delete the user's sites.

Tested in Grok Build 1.0.88 on Nov 18, 2026, on a free xAI account, installed with `grok plugin install` from a copy of this folder: it signed in with a Tiiny Host account in the browser, published a page and deleted it.

## Install

Once xAI lists it: in Grok Build's plugin browser, search "Tiiny Host" and install.

## What it contains

| File | Purpose |
|---|---|
| `.grok-plugin/plugin.json` | The plugin's name, description, author and license |
| `.mcp.json` | The address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Grok |
| `LICENSE` | MIT |

## Network and credentials

The plugin runs no code and no hooks on the user's machine. It connects only to `https://mcp.tiiny.host/oauth`, with the user's own Tiiny Host sign-in. It asks for no keys and reads no files or environment variables.

## How it gets listed

xAI lists plugins through a pull request to its catalog, https://github.com/xai-org/plugin-marketplace, adding one entry to `.grok-plugin/marketplace.json`. The entry points at this folder of this repository at a fixed commit, so nothing is copied:

```json
{
  "name": "tiiny-host",
  "description": "Publish files as live websites on Tiiny Host, and list, update or delete your Tiiny Host sites.",
  "category": "deployment",
  "source": {
    "source": "url",
    "url": "https://github.com/Tiiny-Host/skills.git",
    "sha": "<full 40-character commit SHA of this repository>",
    "path": "plugins/grok-build"
  },
  "homepage": "https://tiiny.host",
  "keywords": ["tiiny host", "tiiny.host", "tiiny"],
  "domains": ["tiiny.host", "tiiny.site"]
}
```

With `domains` set, Grok Build can suggest the plugin when the user mentions a tiiny.host or tiiny.site link. xAI's rules: https://github.com/xai-org/plugin-marketplace/blob/main/CONTRIBUTING.md
