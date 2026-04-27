---
title: SKILL — obsidian-vault-workflow
tags:
  - skill
  - obsidian
  - claude-code
type: file-doc
---

# SKILL — obsidian-vault-workflow

## Overview

Skill המגדיר פרוטוקול חובה לניהול vault ב-Obsidian. מורכב משני phases: לפני כל משימה (קריאת הקשר) ואחרי כל משימה (כתיבת session log). מבטיח שה-vault משמש כזיכרון ארוך-טווח של הפרויקט.

## Open Questions

- none

## קובץ נמצא ב

`.claude/skills/obsidian-vault-workflow/SKILL.md`

## תפקיד

**Phase 1 (לפני משימה):** מזהה topic, מחפש קובץ קיים ב-vault, קורא Meeting Notes אחרונים.  
**Phase 2 (אחרי משימה):** כותב session log entry עם תאריך, סטטוס, wikilinks, ומעדכן Overview.

## מבנה vault שמגדיר הסקיל

```
vault/
├── Meeting Notes/    ← קוד, ארכיטקטורה, החלטות
├── Content Briefs/   ← briefs עריכתיים
├── Publishing Log/   ← תוצאות פרסום
└── Brand Guidelines/ ← קול, ויזואלי, טון
```

## קבצים קשורים

- [[skill-obsidian-markdown]] — סינטקס Markdown לכתיבת ה-vault notes
- [[skill-obsidian-bases]] — יצירת views של ה-vault
- [[skills-directory]] — תיקיית האב של ה-skill
