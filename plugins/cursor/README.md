# Tiiny Host plugin for Cursor

Adds Tiiny Host to the Cursor CLI, Cursor's coding agent for the terminal; its command is `agent`. Ask the agent to put a page online and get a live link on tiiny.site, or to delete one of your sites. The plugin connects the agent to the Tiiny Host MCP server, which gives it four tools: `publish_site`, `list_sites`, `update_site` and `delete_site`.

## Install

Clone this repository, then start the Cursor CLI with the plugin folder:

```bash
git clone https://github.com/Tiiny-Host/skills.git
agent --plugin-dir ./skills/plugins/cursor
```

`--plugin-dir` loads the plugin only for that session. Start the agent this way each time, with the path to the `plugins/cursor` folder of your clone.

## Sign in

Before the first use, open `/mcp` in the agent, select the Tiiny Host server and choose Login. The agent shows a sign-in link: open it in the browser and sign in with your Tiiny Host account. No API key is needed.

## Use

Ask in plain words, for example:

- "Make a one-page site for my bakery and publish it on Tiiny Host."
- "Delete mysite.tiiny.site from Tiiny Host."

## What it contains

| File | Purpose |
|---|---|
| `.cursor-plugin/plugin.json` | The plugin's name, description, author, license and logo |
| `mcp.json` | The address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Cursor's agent |
| `assets/logo.png` | The Tiiny Host icon |
| `LICENSE` | MIT |

## Network and credentials

The plugin runs no code and no hooks on your machine. The agent connects only to `https://mcp.tiiny.host/oauth`, signed in as you, and can only reach sites owned by your Tiiny Host account. Files you ask to publish become public websites on tiiny.site; each publish sends one file of up to 15 MB. The plugin asks for no keys.

Privacy policy: https://tiiny.host/privacypolicy.html
Support: support@tiiny.host
