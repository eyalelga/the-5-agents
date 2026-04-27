# Nano Banana Skill & Yuval Agent

## Overview

הוספת שני רכיבים לפרויקט: (1) Skill בשם nano-banana-2 לייצור תמונות דרך MCP, ו-(2) סוכן קריאייטיב בשם יובל שמשתמש ב-Skill ושומר על עקביות ויזואלית בין תמונות.

## Open Questions

- מהו ה-MCP package הנכון עבור Google Nano Banana 2? (המודל לא מוכר כמודל Google קיים — ייתכן שם פנימי או מודל עתידי)
- מה ה-API key וה-endpoint הנכון?
- האם יש אפשרות לשלוט ב-resolution ו-style נוספים דרך ה-MCP?

## Session Log

### 2026-04-27 — יצירת nano-banana-2 skill ו-yuval agent [shipped]

- **What was done:** נוצרו `.claude/skills/nano-banana-2/SKILL.md`, `.claude/agents/yuval.md`, תיקיות `reference/` ו-`outputs/`. עודכן `settings.json` עם MCP server config (placeholder). עודכן ceo_agent.md עם יובל ברג'יסטרי. עודכן CLAUDE.md.
- **Decisions:** MCP config נוצר כ-placeholder כי "Google Nano Banana 2" אינו מודל ידוע — התשתית מוכנה לעדכון כשיאושר ה-endpoint. יובל נבנה כ-5-step workflow: scan → analyze → craft prompt → generate → report.
- **Notes / Caveats:** `GOOGLE_API_KEY` ב-settings.json צריך להיות מוחלף בערך אמיתי. שם ה-npm package `@google/nano-banana-mcp` הוא placeholder.
- **Related:** [[ceo-agent-creation]], [[skills-directory]], [[agents-directory]]
