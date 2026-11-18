# Tiiny Host extension for Gemini CLI

Adds Tiiny Host to Gemini CLI, Google's coding agent for the terminal. It points Gemini at the Tiiny Host MCP server to publish, list, update and delete the user's sites.

Tested in Gemini CLI 0.68.0 on Nov 17, 2026, installed from a clone of this repository: it signed in with a Tiiny Host account in the browser, published a page, listed the account's sites and deleted the page. That run used the older `httpUrl` server field; on Nov 18, 2026, with the current `url` field, it installed from a copy of this folder, signed in, published a page and deleted it. Replacing a site and installing from GitHub haven't been tried yet.

## Install

Tested on Gemini CLI 0.68.0. On older versions the extension may not connect; if so, update Gemini CLI.

Once this folder is released (see [How it is released](#how-it-is-released)):

```bash
gemini extensions install https://github.com/Tiiny-Host/skills
```

The extension then shows in `gemini extensions list`. Before the first use, run `/mcp auth tiiny-host` in Gemini CLI and sign in with your Tiiny Host account in the browser. No API key is needed.

## What it contains

| File | Purpose |
|---|---|
| `gemini-extension.json` | The extension's name and the address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | Publishing instructions for Gemini |

## How it is released

Gemini CLI reads `gemini-extension.json` only from the root of a repository or of a release archive. Here the extension lives in a folder, so, per Gemini CLI's docs, the install command above takes it from the latest GitHub release of this repository (not tried yet: there is no release):

1. Zip the contents of this folder, so that `gemini-extension.json` is at the top of the zip:
   ```bash
   cd plugins/gemini-cli && zip -r ../../tiiny-host-gemini-cli.zip .
   ```
2. Create a GitHub release of this repository and attach the zip as its only file.
3. For the gallery at https://geminicli.com/extensions, add the topic `gemini-cli-extension` to this repository. The gallery checks tagged repositories daily.

Check the folder before each release:

```bash
gemini extensions validate ./plugins/gemini-cli
```
