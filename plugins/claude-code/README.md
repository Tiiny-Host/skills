# Tiiny Host plugin for Claude Code

Adds Tiiny Host to Claude Code. A developer can say "put this page online" and get a live link on tiiny.site, or ask Claude to delete one of their sites. The server also has tools to list sites and to replace a site with a new version.

## Install

In Claude Code, once this repository's main branch has the plugin:

```
/plugin install tiiny-host --marketplace Tiiny-Host/skills
```

The plugin then shows in `/plugin`, and its server in `/mcp`. Before the first use, sign in there: select the Tiiny Host server, authenticate, and sign in with your Tiiny Host account in the browser. No API key is needed.

The repository root holds `.claude-plugin/marketplace.json`, which lists this folder, so Claude Code installs it straight from this repository. The same folder can be submitted to Anthropic's plugin directory.

## What it contains

| File | Purpose |
|---|---|
| `.claude-plugin/plugin.json` | The plugin's name, description, author and icon |
| `.mcp.json` | The address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | How Claude should publish: confirm first, one site at a time |
| `assets/logo.png` | The Tiiny Host icon shown in the plugin directory |

## What it sends where

The plugin runs no code on the user's computer. Claude talks only to the Tiiny Host server at `https://mcp.tiiny.host/oauth`, signed in as the user. Files the user asks to publish become public websites on tiiny.site. Tiiny Host only reaches sites owned by the account the user signed in with. Each publish sends one file of up to 15 MB.

Privacy policy: https://tiiny.host/privacypolicy.html
Support: support@tiiny.host
