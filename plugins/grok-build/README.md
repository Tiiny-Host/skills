# Tiiny Host plugin for Grok Build

Adds Tiiny Host to Grok Build, xAI's coding agent for the terminal. Ask Grok to put a page online and get a live link on tiiny.site, or to delete one of your sites. The plugin connects Grok to the Tiiny Host MCP server, which gives it four tools: `publish_site`, `list_sites`, `update_site` and `delete_site`.

## Install

```bash
grok plugin install 'Tiiny-Host/skills#plugins/grok-build' --trust
```

`--trust` confirms that you trust the plugin. Grok Build requires it to install a plugin from GitHub, because plugins can add MCP servers, skills and hooks; this one adds one MCP server and one skill, and no hooks.

## Sign in

The first time Grok uses Tiiny Host, it opens the browser to sign in with your Tiiny Host account. No API key is needed.

## Use

Ask in plain words, for example:

- "Make a one-page site for my bakery and publish it on Tiiny Host."
- "Delete mysite.tiiny.site from Tiiny Host."

## What it contains

| File | Purpose |
|---|---|
| `.grok-plugin/plugin.json` | The plugin's name, description, author and license |
| `.mcp.json` | The address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Grok |
| `LICENSE` | MIT |

## Network and credentials

The plugin contains no scripts, executables or hooks. Grok connects to `https://mcp.tiiny.host/oauth`, the Tiiny Host MCP server, signed in as you, and can only reach sites owned by your Tiiny Host account. To sign you in, Grok also connects to `https://api.tiiny.host`, the sign-in server that the MCP server names: there it registers as a client, you sign in in the browser, and it gets its access token. Files you ask to publish become public websites on tiiny.site; each publish sends one file of up to 15 MB. The plugin asks for no keys.

Privacy policy: https://tiiny.host/privacypolicy.html
Support: support@tiiny.host
