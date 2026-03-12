<picture>
  <img width="250px" alt="Tiiny.Host Logo" src="https://tiiny.host/assets/logo.png">
</picture>

# Agent Skills

A collection of [Agent Skills](https://agentskills.io/) and agent integrations for Tiiny Host.

## What are Agent Skills?

Skills are folders of instructions, scripts, and resources that agents can discover and use to do things more accurately and efficiently. Once installed, skills are automatically invoked by the agent upon detection of relevant tasks.

It all starts with the `SKILL.md` file in the skill's directory. It's the entry point and allows agents to progressively discover information as needed.

## Available Skills

### Publish Skill

A simple skill to deploy your HTML static app or share 100+ other file types (e.g. PDF, ZIP, DOCX) online.

## Installation

### Claude Code

```bash
mkdir -p ~/.claude/skills/tiiny-host
curl -sL https://raw.githubusercontent.com/tiinyhost/skills/main/skills/SKILL.md \
  -o ~/.claude/skills/tiiny-host/SKILL.md
```

Then invoke it in Claude Code with `/tiiny-host` or let Claude auto-detect when you ask to publish or deploy something.

### Other agents (agentskills.io)

```bash
npx skills add tiiny-host/skills
```
