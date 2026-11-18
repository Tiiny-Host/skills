# Tiiny Host plugin for Claude Code

Adds Tiiny Host to Claude Code, Anthropic's coding agent. Ask Claude to put a page online and get a live link on tiiny.site, or to delete one of your sites. The plugin connects Claude to the Tiiny Host MCP server, which gives it four tools: `publish_site`, `list_sites`, `update_site` and `delete_site`.

## Install

```bash
claude plugin install tiiny-host --marketplace Tiiny-Host/skills
```

The plugin then shows in `/plugin`, and its server in `/mcp`.

## Sign in

Before the first use, open `/mcp` in Claude Code, select the Tiiny Host server, authenticate and sign in with your Tiiny Host account in the browser. No API key is needed.

## Use

Ask in plain words, for example:

- "Make a one-page site for my bakery and publish it on Tiiny Host."
- "Delete mysite.tiiny.site from Tiiny Host."

## What it contains

| File | Purpose |
|---|---|
| `.claude-plugin/plugin.json` | The plugin's name, description, author and icon |
| `.mcp.json` | The address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Claude |
| `assets/logo.png` | The Tiiny Host icon |
| `LICENSE` | MIT |

## Network and credentials

The plugin contains no scripts, executables or hooks. Claude connects to `https://mcp.tiiny.host/oauth`, the Tiiny Host MCP server, signed in as you, and can only reach sites owned by your Tiiny Host account. To sign you in, Claude also connects to `https://api.tiiny.host`, the sign-in server that the MCP server names: there it registers as a client and gets its access token, while you sign in and allow access on tiiny.host in your browser. Files you ask to publish become public websites on tiiny.site; each publish sends one file of up to 15 MB. The plugin asks for no keys.

Privacy policy: https://tiiny.host/privacypolicy.html
Terms of service: https://tiiny.host/termsofservice.html
Support: support@tiiny.host
