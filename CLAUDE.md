# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Mandatory Workflow — Obsidian Vault Protocol

**At the start of every session and before executing any command**, follow the `obsidian-vault-workflow` skill protocol located at `.claude/skills/obsidian-vault-workflow/SKILL.md`:

1. **Phase 1 (Before task):** Identify the topic, locate or create the topic file in `vault/Meeting Notes/`, read recent context.
2. **Phase 2 (After task):** Append a dated session log entry to the topic file with wikilinks to related vault notes.

The vault at `vault/` is the long-term memory of this project. Skipping this protocol is not allowed.

**CLAUDE.md must be updated after every change to the project** — agents added, skills installed, architecture decisions made.

## Project Overview

"The 5 Agents" — מערכת רב-סוכנים המבוססת על Claude Code. סוכן ראשי בשם **Reuven** (CEO) מנהל ומתאם 4 סוכנים מתמחים: חן, יובל, יעל, וגיא. הפרויקט משתמש ב-Obsidian כ-vault לזיכרון ארוך-טווח.

## Architecture

```
the 5 agents/
├── .claude/
│   ├── agents/
│   │   ├── ceo_agent.md       ← Reuven — CEO Master Agent (orchestrator)
│   │   ├── chen.md            ← Chen — Web Researcher
│   │   ├── yuval.md           ← Yuval — Creative Image Agent
│   │   ├── yael.md            ← Yael — Content Writer (LLM-only)
│   │   └── guy.md             ← Guy — QA Agent (final gatekeeper)
│   ├── skills/
│   │   ├── obsidian-vault-workflow/   ← mandatory session protocol
│   │   ├── obsidian-markdown/         ← Obsidian MD syntax guide
│   │   ├── obsidian-bases/            ← Obsidian Bases (.base files)
│   │   ├── skill-creator/             ← build, test & optimize new skills
│   │   ├── nano-banana-2/             ← image generation via Gemini 2.5 Flash MCP
│   │   └── superpowers/               ← 14 methodology skills (TDD, planning, debugging...)
│   └── settings.json          ← permissions, hooks & MCP servers
├── chen/
│   └── Memory/
│       └── searches.md        ← Chen's personal search log (deduplication + history)
├── guy/
│   └── QA_Reports/            ← Guy's QA report archive (one file per article per round)
├── Content/                   ← raw articles waiting for Yael to rewrite (Chen saves here)
│   └── Ready/                 ← originals archived after Yael processes them
├── Output/                    ← Yael's finished rewritten articles
├── reference/                 ← reference images for style analysis (input to Yuval)
├── outputs/                   ← generated images (output from Yuval)
├── vault/                     ← long-term memory (Obsidian)
│   ├── Files/                 ← documentation per project file
│   └── Meeting Notes/         ← session logs & decisions
└── CLAUDE.md                  ← this file (always keep updated)
```

### CEO Agent — Reuven

The primary orchestrator. **Always invoked first** for any task. Analyzes requests, decomposes into sub-tasks, delegates to specialized agents, and synthesizes results. Defined at [`.claude/agents/ceo_agent.md`](.claude/agents/ceo_agent.md).

Reads the user's global profile before tasks to tailor output:
`C:/Users/User/.claude/profile/` — personality, interests, code style.

### Sub-Agents

| Agent | File | Specialty | Tools |
|-------|------|-----------|-------|
| Chen | `.claude/agents/chen.md` | Web research — searches internet for articles on request from Reuven, saves raw content + source URL to `Content/`, logs to `chen/Memory/searches.md` | WebSearch, WebFetch, Read, Write, Glob |
| Yuval | `.claude/agents/yuval.md` | Image generation — scans `reference/`, builds style-consistent prompts, generates via nano-banana-2, saves to `outputs/` | Read, Write, Glob, Bash |
| Yael | `.claude/agents/yael.md` | Content writing — rewrites raw articles from `Content/` in project voice, calls Yuval for images, saves to `Output/`, archives originals to `Content/Ready/` | Read, Write, Glob, Task |
| Guy | `.claude/agents/guy.md` | QA — final gatekeeper. Receives Yael's `Output/` article + original brief, runs 10-point checklist, saves report to `guy/QA_Reports/`, returns ✅ Approved or ❌ Requires Fix. Max 3 rounds. | Read, Write, Glob |

### User Global Profile

Located at `C:/Users/User/.claude/profile/` (outside the repo — global across all projects):

| File | Content |
|------|---------|
| `personality.md` | אישיות, אופי, ערכים, קול |
| `interests.md` | תחומי עניין, השראות, פרויקטים |
| `code-style.md` | העדפות קוד, שפות, מה לא לעשות |

### MCP Servers

| Server | Purpose | Package |
|--------|---------|---------|
| nano-banana-2 | Gemini 2.5 Flash image generation | `nano-banana-mcp` |

Requires `GEMINI_API_KEY` in `.env`.

## Commands

- **Add an agent:** Create `.claude/agents/<name>.md` with frontmatter (`name`, `description`, `tools`) and a system prompt. Register it in the CEO agent's Sub-Agent Registry and in this file.
- **Update vault:** Follow `obsidian-vault-workflow` — append to `vault/Meeting Notes/<topic>.md`.
- **Update profile:** Edit files in `C:/Users/User/.claude/profile/` directly.
- **Push changes:** `git add` → `git commit` → `git push` (permitted in settings.json).
