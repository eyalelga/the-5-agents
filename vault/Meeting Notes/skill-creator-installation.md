# Skill Creator Installation

## Overview

התקנת ה-skill-creator מ-anthropics/skills GitHub repo. הסקיל מאפשר יצירה, שיפור, ובדיקה של skills חדשים עם eval framework מלא.

## Open Questions

- none

## Session Log

### 2026-04-27 — התקנת skill-creator מ-GitHub [shipped]

- **What was done:** הורדו 17 קבצים מ-`https://github.com/anthropics/skills/tree/main/skills/skill-creator` ישירות עם curl אל `.claude/skills/skill-creator/`. כולל SKILL.md, agents (analyzer, comparator, grader), references/schemas.md, scripts Python, ו-eval-viewer.
- **Decisions:** שימוש ב-curl ישיר במקום WebFetch בגלל מגבלות ה-WebFetch tool עם raw content.
- **Notes / Caveats:** הסקריפטים Python דורשים `claude` CLI מותקן ו-Python 3. הסקיל עצמו (SKILL.md) פועל ב-Claude Code ללא תלויות נוספות.
- **Related:** [[skills-directory]], [[project-file-documentation]]
