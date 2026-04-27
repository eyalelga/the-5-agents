# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Mandatory Workflow — Obsidian Vault Protocol

**At the start of every session and before executing any command**, follow the `obsidian-vault-workflow` skill protocol located at `.claude/skills/obsidian-vault-workflow/SKILL.md`:

1. **Phase 1 (Before task):** Identify the topic, locate or create the topic file in `vault/Meeting Notes/`, read recent context.
2. **Phase 2 (After task):** Append a dated session log entry to the topic file with wikilinks to related vault notes.

The vault at `vault/` is the long-term memory of this project. Skipping this protocol is not allowed.

**CLAUDE.md must be updated after every change to the project** — agents added, skills installed, architecture decisions made.

## Project Overview

"The 5 Agents" — מערכת רב-סוכנים המבוססת על Claude Code. סוכן ראשי בשם **Eyal** (CEO) מנהל ומתאם עד 4 סוכנים מתמחים. הפרויקט משתמש ב-Obsidian כ-vault לזיכרון ארוך-טווח.

## Architecture

```
the 5 agents/
├── .claude/
│   ├── agents/
│   │   └── ceo_agent.md       ← Eyal — CEO Master Agent (orchestrator)
│   ├── agents/
│   │   ├── ceo_agent.md       ← Eyal — CEO Master Agent (orchestrator)
│   │   └── yuval.md           ← Yuval — Creative Image Agent
│   ├── skills/
│   │   ├── obsidian-vault-workflow/   ← mandatory session protocol
│   │   ├── obsidian-markdown/         ← Obsidian MD syntax guide
│   │   ├── obsidian-bases/            ← Obsidian Bases (.base files)
│   │   ├── skill-creator/             ← build, test & optimize new skills
│   │   └── nano-banana-2/             ← image generation via Google Nano Banana 2 MCP
│   └── settings.json          ← permissions, hooks & MCP servers
├── reference/                 ← reference images for style analysis (input to Yuval)
├── outputs/                   ← generated images (output from Yuval)
├── vault/                     ← long-term memory (Obsidian)
│   ├── Files/                 ← documentation per project file
│   └── Meeting Notes/         ← session logs & decisions
└── CLAUDE.md                  ← this file (always keep updated)
```

### CEO Agent — Eyal

The primary orchestrator. **Always invoked first** for any task. Analyzes requests, decomposes into sub-tasks, delegates to specialized agents, and synthesizes results. Defined at `.claude/agents/ceo_agent.md`.

Sub-agents will be registered in the CEO agent's Sub-Agent Registry table as they are created.

### Sub-Agents

| Agent | File | Specialty |
|-------|------|-----------|
| Yuval | `.claude/agents/yuval.md` | Image generation with style consistency |

### MCP Servers

| Server | Purpose | Config key |
|--------|---------|------------|
| nano-banana-2 | Google Nano Banana 2 image generation | `mcpServers.nano-banana-2` in settings.json |

> **Action required:** Replace `YOUR_API_KEY_HERE` in `.claude/settings.json` with a real API key, and verify the MCP package name `@google/nano-banana-mcp` once the model is officially available.

## Commands

- **Add an agent:** Create `.claude/agents/<name>.md` with frontmatter (`name`, `description`, `tools`) and a system prompt. Register it in the CEO agent's Sub-Agent Registry.
- **Update vault:** Follow `obsidian-vault-workflow` — append to `vault/Meeting Notes/<topic>.md`.
- **Push changes:** `git add` → `git commit` → `git push` (permitted in settings.json).
