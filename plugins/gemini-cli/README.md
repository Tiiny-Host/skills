# Tiiny Host extension for Gemini CLI

Adds Tiiny Host to Gemini CLI, Google's coding agent for the terminal. A developer can say "publish this page" and get a live link on tiiny.site, and ask Gemini to list, update or delete their Tiiny Host sites. Gemini asks before it publishes, replaces or deletes anything.

## Install

Once this folder is released (see [How it is released](#how-it-is-released)):

```bash
gemini extensions install https://github.com/Tiiny-Host/skills
```

The extension then shows in `gemini extensions list`, and its server in `/mcp`. The first time Gemini uses Tiiny Host, the user signs in with their Tiiny Host account in the browser. No API key is needed.

## What it contains

| File | Purpose |
|---|---|
| `gemini-extension.json` | The extension's name and the address of the Tiiny Host server: `https://mcp.tiiny.host/oauth` |
| `skills/tiiny-host/SKILL.md` | How Gemini should publish: confirm first, one site at a time |

## How it is released

Gemini CLI reads `gemini-extension.json` only from the root of a repository or of a release archive. Here the extension lives in a folder, so the install command above takes it from the latest GitHub release of this repository:

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
