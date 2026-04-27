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

## Session — 2026-04-27

### Task: שכתוב מאמר CRM

עיבוד מאמר עברי על CRM — שכתוב מלא, יצירת תמונות, שמירה ל-Output.

**קובץ מקור:** `Content/what-is-crm.md`
**פלט:** `Output/what-is-crm.md`
**תמונות שנוצרו:**
- `Output/what-is-crm-image-1.png` — לוח בקרה CRM, dark mode (יובל)
- `Output/what-is-crm-image-2.png` — דיאגרמת זרימת אוטומציה (יובל)
**ארכיון:** `Content/Ready/what-is-crm.md`

### הערות

- יעל אינה agent type רשום במערכת Claude Code — הזרימה בוצעה ישירות
- יובל הצליח לייצר שתי תמונות — שינה את שם המודל ל-`gemini-2.5-flash-image`
- אין STYLE.md ב-Content/ — שימוש בסגנון ברירת מחדל של יעל

### Wikilinks

[[yael-agent-creation]] | [[image-generation]] | [[nano-banana-skill-yuval-agent]]

## Session — 2026-04-27 (המשך) — סוכנת חן + שינוי שם CEO

### שינוי שם CEO

הסוכן "אייל" שונה ל-**ראובן** בכל הקבצים:
- `.claude/agents/ceo_agent.md` — frontmatter + system prompt
- `CLAUDE.md` — Project Overview + Architecture

### סוכנת חן — Web Researcher

**קבצים שנוצרו:**
- `.claude/agents/chen.md` — הגדרת הסוכנת
- `chen/Memory/searches.md` — יומן חיפושים (ריק, מוכן לשימוש)

**עדכונים:**
- `ceo_agent.md` — חן נרשמה ב-Sub-Agent Registry
- `CLAUDE.md` — עודכנה ארכיטקטורת הפרויקט

**Flow של חן:**
ראובן → חן (בדיקת זיכרון → חיפוש → שמירה ב-Content/ → תיעוד) → ראובן → יעל → יובל (אם צריך) → Output/

### Wikilinks

[[ceo-agent-creation]] | [[yael-agent-creation]] | [[image-generation]]

## Session — 2026-04-27 (סיום) — סוכן גיא + השלמת מערכת 5 הסוכנים

### סוכן גיא — QA Agent

**קבצים שנוצרו:**
- `.claude/agents/guy.md` — הגדרת הסוכן (7 שלבי עבודה, צ'קליסט 10 נקודות, בקרת לולאה)
- `guy/QA_Reports/` — תיקיית ארכיון דוחות QA

**עדכונים:**
- `ceo_agent.md` — גיא נרשם ב-Sub-Agent Registry
- `CLAUDE.md` — עודכנו: Project Overview, Architecture tree, Sub-Agents table

### Flow מלא של המערכת (5 סוכנים פעילים)

ראובן → חן (חיפוש) → יעל (שכתוב) → יובל (תמונות) → גיא (QA) → ראובן → משתמש

**לולאת תיקון:** גיא ❌ → ראובן → יעל → ראובן → גיא (מקס 3 סיבובים)

### הערות

- גיא נבנה לפי תוכנית שאושרה ב-Plan Mode
- צ'קליסט 10 נקודות: מבנה, רלוונטיות, תמונות, alt text, סגנון, מקור
- גיא לא קורא לסוכנים אחרים — מדווח בלבד לראובן

### Wikilinks

[[ceo-agent-creation]] | [[yael-agent-creation]] | [[nano-banana-skill-yuval-agent]]
