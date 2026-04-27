# Yael Agent Creation

## Overview

יצירת סוכן יעל — כותבת תוכן LLM-Only שמשכתבת מאמרים גולמיים מ-Content/ בסגנון הפרויקט, מזהה צרכי תמונה ומאציילה ליובל, ושומרת תוצרים ב-Output/. הסוכן השלישי במערכת.

## Open Questions

- האם יש style guide קיים להכניס ל-Content/STYLE.md?
- האם יעל צריכה לעבד מאמרים מרובים ברצף אוטומטי?

## Session Log

### 2026-04-27 — יצירת Yael Content Writer Agent [shipped]

- **What was done:** נוצר `.claude/agents/yael.md` עם 10-שלב workflow. נוצרו תיקיות `Content/`, `Content/Ready/`, `Output/`. עודכנו ceo_agent.md ו-CLAUDE.md. Brainstorming skill הופעל אבל המשתמש ביקש לדלג ל-plain mode.
- **Decisions:** סגנון כתיבה מוגדר ב-system prompt עם אפשרות override דרך `Content/STYLE.md`. יעל מאציילה ליובל דרך Task tool ומשלבת תמונות עם markdown image references.
- **Notes / Caveats:** יעל LLM-only — אין לה כלים חיצוניים מלבד Read/Write/Glob/Task. לתמונות היא תלויה לחלוטין ביובל.
- **Related:** [[ceo-agent-creation]], [[nano-banana-skill-yuval-agent]], [[image-generation]]
