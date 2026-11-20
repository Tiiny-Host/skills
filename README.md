<picture>
  <img width="250px" alt="Tiiny.Host Logo" src="https://tiiny.host/assets/logo.png">
</picture>

# Tiiny Host MCP server, skills and plugins for AI agents

Tiiny Host turns anything an AI agent makes - an HTML page, a PDF, an image, a ZIP of a static site - into a live website on tiiny.site with a link to share. This repository describes Tiiny Host's remote MCP server and holds its [Agent Skill](https://agentskills.io/) and its plugins for coding agents.

## MCP server

Tiiny Host runs a remote MCP server at `https://mcp.tiiny.host/oauth` (Streamable HTTP). It is listed in the official MCP Registry as `host.tiiny/tiiny-host`. The server's code is not in this repository.

### What it does

| Tool | What it does |
|---|---|
| `publish_site` | Publishes one file - an HTML page, a PDF, an image or a ZIP of a static site - as a new public site and returns its link |
| `list_sites` | Lists the sites of your Tiiny Host account with their creation dates, the number of sites and your plan's site limit |
| `update_site` | Replaces all files of one of your sites with a new file; the link stays the same |
| `delete_site` | Deletes one of your sites with all its files |

The server only reaches sites owned by the account you sign in with. Plans have a site limit and a file size limit: over a limit, a new site stays live for one hour in preview mode.

### How to set it up

Add the server to any MCP client that supports remote servers with OAuth. In VS Code, for GitHub Copilot, add it to `.vscode/mcp.json` or to your user MCP configuration:

```json
{
  "servers": {
    "tiiny-host": {
      "type": "http",
      "url": "https://mcp.tiiny.host/oauth"
    }
  }
}
```

On first use, the client opens the Tiiny Host sign-in page in your browser. Sign in with your Tiiny Host account, free or paid, and approve access. The client registers itself, so there is no API key, client ID or secret to enter. Setup for Claude, Claude Code, Codex, Cursor, Windsurf, Zed and other clients: [MCP Connection Guide](https://api-docs.tiiny.host/connection-guide-2259947m0).

### How to use it

Ask your agent in plain words, for example:

- "Make a one-page site for my bakery Sunny Crumbs, we're open 8am to 4pm every day, and publish it on Tiiny Host."
- "What sites do I have on Tiiny Host?"
- "Change my Opening soon page on Tiiny Host to say we're open now."
- "Take down the test page I published on Tiiny Host."

The agent replies with the live `https://<name>.tiiny.site` link.

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

- **MCP server with email sign-in** at `https://mcp.tiiny.host`, for clients without OAuth: the user signs in with a code sent to their email, through the tools `request_otp` and `verify_otp`, and gets the same four tools.
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
