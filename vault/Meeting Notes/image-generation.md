# Image Generation

## Overview

ייצור תמונות באמצעות יובל (Yuval agent) ו-nano-banana-2 MCP (Gemini 2.5 Flash Image API). יובל סורק את reference/, מנתח סגנון, בונה פרומפט ומייצר תמונות ל-outputs/.

## Open Questions

- none

## Session Log

### 2026-04-27 — ייצור תמונת סוס דוהר [shipped]

- **What was done:** הופעל יובל עם בקשה "סוס דוהר". reference/ הייתה ריקה. יובל בנה פרומפט cinematic ושמר את התמונה ב-`outputs/galloping-horse.jpeg` דרך nano-banana-2 MCP (gemini-3.1-flash-image-preview).
- **Decisions:** MCP תוקן לפני הריצה — שם המשתנה שונה מ-GOOGLE_API_KEY ל-GEMINI_API_KEY, ושם הpackage תוקן ל-`nano-banana-mcp`.
- **Notes / Caveats:** כשתיקיית reference/ מכילה תמונות, יובל ישלב את הסגנון שלהן בפרומפט.
- **Related:** [[nano-banana-skill-yuval-agent]], [[ceo-agent-creation]]
