# Tiiny Host plugin for Antigravity

Adds Tiiny Host to the Antigravity CLI, the terminal version of Google's Antigravity coding agent. Ask Antigravity to put a page online and get a live link on tiiny.site, to list your sites, or to delete one. The plugin connects Antigravity to the Tiiny Host MCP server, which gives it four tools: `publish_site`, `list_sites`, `update_site` and `delete_site`.

## Install

From a clone of this repository:

```bash
git clone https://github.com/Tiiny-Host/skills.git
agy plugin install ./skills/plugins/antigravity
```

The plugin then shows in `agy plugin list`.

## Sign in

Before the first use, open `/plugin` in the Antigravity CLI, expand tiiny-host under Installed, choose Sign in and sign in with your Tiiny Host account in the browser. No API key is needed.

## Use

Ask in plain words, for example:

- "Make a one-page site for my bakery and publish it on Tiiny Host."
- "What sites do I have on Tiiny Host?"
- "Delete mysite.tiiny.site from Tiiny Host."

## What it contains

| File | Purpose |
|---|---|
| `plugin.json` | The plugin's name, description, logo, starter prompts, author and license |
| `mcp_config.json` | The address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Antigravity |
| `assets/logo.png` | The Tiiny Host icon |
| `LICENSE` | MIT |

## Network and credentials

The plugin contains no scripts, executables or hooks. Antigravity connects to `https://mcp.tiiny.host/oauth`, the Tiiny Host MCP server, signed in as you, and can only reach sites owned by your Tiiny Host account. To sign you in, Antigravity also connects to `https://api.tiiny.host`, the sign-in server that the MCP server names: there it registers as a client and gets its access token, while you sign in and allow access on tiiny.host in your browser. Files you ask to publish become public websites on tiiny.site; each publish sends one file of up to 15 MB. The plugin asks for no keys.

Privacy policy: https://tiiny.host/privacypolicy.html
Support: support@tiiny.host
