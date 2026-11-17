<picture>
  <img width="250px" alt="Tiiny.Host Logo" src="https://tiiny.host/assets/logo.png">
</picture>

# Tiiny Host skills and plugins for AI agents

Tiiny Host turns anything an AI agent makes - an HTML page, a PDF, an image, a ZIP of a static site - into a live website on tiiny.site with a link to share. This repository holds Tiiny Host's [Agent Skill](https://agentskills.io/) and its plugins for coding agents.

## What is in this repository

| Folder | What it adds | Install |
|---|---|---|
| [skills/](skills/) | The publish skill: any agent that reads Agent Skills can publish, update, list and delete sites through the Tiiny Host API | [Install the skill](#install-the-skill) |
| [plugins/claude-code/](plugins/claude-code/) | Plugin for Claude Code | `/plugin install tiiny-host --marketplace Tiiny-Host/skills`, once the plugin is on main |
| [plugins/gemini-cli/](plugins/gemini-cli/) | Extension for Gemini CLI, not tested in Gemini CLI yet | `gemini extensions install https://github.com/Tiiny-Host/skills`, once the folder is released ([how](plugins/gemini-cli/#how-it-is-released)) |
| [plugins/grok-build/](plugins/grok-build/) | Plugin for Grok Build, not tested in Grok Build yet | Once listed: from xAI's plugin catalog |
| [plugins/cursor/](plugins/cursor/) | Plugin for Cursor, not tested in Cursor yet | Once listed: from the Cursor Marketplace |
| [plugins/antigravity/](plugins/antigravity/) | Plugin for Antigravity, Google's agent that replaces Gemini CLI; not tested in Antigravity yet | Once listed: from Google's Antigravity Marketplace, `agy plugin install tiiny-host` |

The skill and the plugins work differently. The skill calls the Tiiny Host API with curl: a first-time user publishes with just an email, and an API key makes their sites permanent. The plugins connect the agent to the Tiiny Host MCP server, where the user signs in with their Tiiny Host account in the browser; so far this is tested in Claude Code. Each plugin folder has its own README.

`.claude-plugin/marketplace.json` lists the Claude Code plugin, so Claude Code installs it straight from this repository (tested from a clone). `.cursor-plugin/marketplace.json` points Cursor to its plugin the same way.

## Tiiny Host in AI assistants

- **MCP server** at `https://mcp.tiiny.host`, for any assistant that supports MCP. It has six tools: `request_otp` and `verify_otp` sign the user in with a code sent to their email, then `list_sites`, `publish_site`, `update_site` and `delete_site`. How to add it to Claude, Claude Code, Codex, Cursor, VS Code, Windsurf, Zed and others: [MCP Connection Guide](https://api-docs.tiiny.host/connection-guide-2259947m0). The plugins in this repository use the same server at `https://mcp.tiiny.host/oauth`, where the user signs in through the browser instead of with a code.
- **API**: [api-docs.tiiny.host](https://api-docs.tiiny.host) - upload, update, delete and list sites. The skill uses it.
- **Chrome extensions**: publish code from ChatGPT, Claude, Gemini and Grok chats, or any file from the side panel - [Tiiny Labs Limited in the Chrome Web Store](https://chromewebstore.google.com/publisher/tiiny-labs-limited/u1f4450f98f72da9912e9bce021b88055).

## What are Agent Skills?

Skills are folders of instructions, scripts, and resources that agents can discover and use to do things more accurately and efficiently. Once installed, skills are automatically invoked by the agent upon detection of relevant tasks.

It all starts with the `SKILL.md` file in the skill's directory. It's the entry point and allows agents to progressively discover information as needed.

## Install the skill

### Claude Code

```bash
mkdir -p ~/.claude/skills/tiiny-host
curl -sL https://raw.githubusercontent.com/Tiiny-Host/skills/main/skills/SKILL.md \
  -o ~/.claude/skills/tiiny-host/SKILL.md
```

Then invoke it in Claude Code with `/tiiny-host` or let Claude auto-detect when you ask to publish or deploy something.

### Other agents (agentskills.io)

```bash
npx skills add tiiny-host/skills
```
