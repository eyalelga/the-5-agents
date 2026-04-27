---
title: .claude/settings.json
tags:
  - config
  - claude-code
type: file-doc
---

# .claude/settings.json

## Overview

קובץ הגדרות Claude Code ברמת הפרויקט. מגדיר הרשאות לפקודות Bash ו-MCP, hooks, ועוד. נקרא אוטומטית על ידי Claude Code בכל פתיחת סשן בפרויקט.

## Open Questions

- none

## קובץ נמצא ב

`.claude/settings.json`

## תפקיד

שולט על אילו פקודות Claude Code מורשה להריץ ללא אישור מפורש מהמשתמש. כרגע מכיל הרשאה ל-`git push`.

## מבנה נוכחי

```json
{
  "permissions": {
    "allow": [
      "Bash(git push *)"
    ]
  }
}
```

## קבצים קשורים

- [[claude-md]] — קובץ ה-CLAUDE.md שעובד יחד עם הגדרות אלו
- [[agents-directory]] — תיקיית agents שמנוהלת תחת `.claude/`
- [[skills-directory]] — תיקיית skills שמנוהלת תחת `.claude/`
