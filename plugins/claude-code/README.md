# Tiiny Host plugin for Claude Code

Adds Tiiny Host to Claude Code. A developer can say "publish this build" or "put this page online" and get a live link on tiiny.site. Claude can also list their Tiiny Host sites, replace a site with a new version, or delete one. Claude asks before it publishes, replaces or deletes anything.

## Install

In Claude Code:

```
/plugin install tiiny-host --marketplace Tiiny-Host/skills
```

The plugin then shows in `/plugin`, and its server in `/mcp`. The first time Claude uses Tiiny Host, the user signs in with their Tiiny Host account in the browser. No API key is needed.

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
