<picture>
  <img width="250px" alt="Tiiny.Host Logo" src="https://tiiny.host/assets/logo.png">
</picture>

# Tiiny Host skills and plugins for AI agents

Tiiny Host turns anything an AI agent makes - an HTML page, a PDF, an image, a ZIP of a static site - into a live website on tiiny.site with a link to share. This repository holds Tiiny Host's [Agent Skill](https://agentskills.io/) and its plugins for coding agents.

## What is in this repository

| Folder | What it adds | Install |
|---|---|---|
| [skills/](skills/) | The publish skill, for agents that read Agent Skills | [Install the skill](#install-the-skill) |
| [plugins/claude-code/](plugins/claude-code/) | Plugin for Claude Code | `claude plugin install tiiny-host --marketplace Tiiny-Host/skills` |
| [plugins/grok-build/](plugins/grok-build/) | Plugin for Grok Build | `grok plugin install 'Tiiny-Host/skills#plugins/grok-build' --trust` |
| [plugins/gemini-cli/](plugins/gemini-cli/) | Extension for Gemini CLI | `gemini extensions install https://github.com/Tiiny-Host/skills` |
| [plugins/antigravity/](plugins/antigravity/) | Plugin for the Antigravity CLI | [From a clone of this repository](plugins/antigravity/#install) |
| [plugins/cursor/](plugins/cursor/) | Plugin for the Cursor CLI | [Loaded from a clone of this repository](plugins/cursor/#install) |

The plugins connect the agent to the Tiiny Host MCP server at `https://mcp.tiiny.host/oauth`: you sign in with your Tiiny Host account in the browser, and no API key is needed. The skill calls the Tiiny Host API with curl. With just an email that has no Tiiny Host account yet, it publishes a site that stays live for one hour; for permanent sites, it signs you in with a code sent to your email and uses your Tiiny Host API key. In Claude Code you can use either one. Each plugin folder has its own README.

`.claude-plugin/marketplace.json` makes this repository a plugin marketplace for Claude Code: that is how the install command above finds the plugin.

## Other ways to use Tiiny Host with AI

- **MCP server** for any assistant that supports MCP, at two addresses. At `https://mcp.tiiny.host` the user signs in with a code sent to their email, through the tools `request_otp` and `verify_otp`. At `https://mcp.tiiny.host/oauth` the user signs in through the browser; the plugins in this repository use this address. Both give the tools `list_sites`, `publish_site`, `update_site` and `delete_site`. How to add it to Claude, Claude Code, Codex, Cursor, VS Code, Windsurf, Zed and others: [MCP Connection Guide](https://api-docs.tiiny.host/connection-guide-2259947m0).
- **API**: [api-docs.tiiny.host](https://api-docs.tiiny.host) - upload, update, delete and list sites. The skill uses it.
- **Chrome extensions**: [Tiiny Labs Limited in the Chrome Web Store](https://chromewebstore.google.com/publisher/tiiny-labs-limited/u1f4450f98f72da9912e9bce021b88055).

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
npx skills add Tiiny-Host/skills
```
