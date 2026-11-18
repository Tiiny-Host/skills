# Tiiny Host extension for Gemini CLI

Adds Tiiny Host to Gemini CLI, Google's open-source coding agent for the terminal. Ask Gemini to put a page online and get a live link on tiiny.site, to list your sites, or to delete one. The extension connects Gemini to the Tiiny Host MCP server, which gives it four tools: `publish_site`, `list_sites`, `update_site` and `delete_site`.

## Install

From a clone of this repository:

```bash
git clone https://github.com/Tiiny-Host/skills.git
gemini extensions install ./skills/plugins/gemini-cli
```

The extension then shows in `gemini extensions list`.

## Sign in

Before the first use, run `/mcp auth tiiny-host` in Gemini CLI and sign in with your Tiiny Host account in the browser. No API key is needed.

## Use

Ask in plain words, for example:

- "Make a one-page site for my bakery and publish it on Tiiny Host."
- "What sites do I have on Tiiny Host?"
- "Delete mysite.tiiny.site from Tiiny Host."

## What it contains

| File | Purpose |
|---|---|
| `gemini-extension.json` | The extension's name and the address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Gemini |
| `LICENSE` | MIT |

## Network and credentials

The extension runs no code and no hooks on your machine. Gemini connects only to `https://mcp.tiiny.host/oauth`, signed in as you, and can only reach sites owned by your Tiiny Host account. Files you ask to publish become public websites on tiiny.site; each publish sends one file of up to 15 MB. The extension asks for no keys.

Privacy policy: https://tiiny.host/privacypolicy.html
Support: support@tiiny.host
