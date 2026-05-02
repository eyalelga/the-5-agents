# Babysitting Tracker

## Overview
אפליקציית HTML SPA עברית למעקב שעות בייביסיטינג עבור שני ילדים: לני (ורוד) ואריאל (כחול). פועלת לגמרי על-ידי localStorage ללא שרת. מבנה 5-tabs עם bottom nav: בית / הוספה / היסטוריה / סיכום / ילדים. כולל פונקציית generateParentReport שמייצרת snapshot HTML ב-window.open עם 2 כרטיסי ילדים, גרף השוואה, טבלת ביקורים, ו-Blob download. עוצב עם Heebo RTL, mobile-first 430px, border-radius 16px.

## Open Questions

- none

## Session Log

### 2026-05-02 — שכתוב מלא v2 — 5 tabs + סיכום כולל + generateParentReport [shipped]
- **What was done:** שכתוב מלא של `Output/babysitting-tracker.html` מגרסה ראשונה (4 tabs) לגרסה שנייה (5 tabs). נוסף Tab 4 "סיכום כולל" עם: ימים מאז הרישום הראשון, כרטיסי סה"כ לכל ילד, ממוצע שבועי, פירוט חודשי. נוסף modal שיתוף עם 3 אפשרויות תקופה. generateParentReport מייצר HTML עצמאי עם נתונים מוטמעים, כפתור הורד (Blob) + הדפס.
- **Decisions:** bottom nav עבר מ-4 לחמישה פריטים (nav-icon הוקטן ל-10px label); חישוב שעות real-time אורע על `input` + `change` (לא רק `change`) לתגובה טובה יותר במובייל; סיכום חודשי ממוין לפי חודש בסדר יורד.
- **Notes / Caveats:** Guy (QA) מותאם למאמרי Markdown — QA של ה-HTML בוצע ישירות על-ידי Reuven עם רשימת 32 פריטים מהבריף. כל הבדיקות עברו.
- **Related:** [[geffen-ai-landing-page]], [[yael-agent-creation]]
