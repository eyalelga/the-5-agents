# Geffen AI Landing Page

## Overview

בניית דף נחיתה פרימיום עבור "Geffen AI Agencies" בהתבסס על PRD מפורט. הדף הוא קובץ HTML עצמאי (React 18 via CDN + Tailwind CDN + Babel Standalone) שמיישם SPA מלא עם Transformation Selector אינטראקטיבי ו-Dynamic Roadmap. נשמר ב-`Output/geffen-ai-landing-page.html`.

## Open Questions

- האם להוסיף כתובת פיזית? — לא מופיעה באתר geffen-global.co.il.
- האם לאחסן ב-GitHub Pages לשיתוף ב-URL ציבורי?

## Session Log

### 2026-04-30 — ייצור תמונת Hero לדף נחיתה Geffen AI [shipped]

- **What was done:** יוצרה תמונת hero בסגנון obsidian + liquid gold דרך Gemini 3.1 Flash Image Preview API (model: `gemini-3.1-flash-image-preview`). הקובץ נשמר ל-`outputs/geffen-hero.png` (839KB, JPEG). קוד ה-CSS ב-`Output/geffen-ai-landing-page.html` עודכן — ה-CSS gradient placeholder הוחלף ב-`background-image: url('../outputs/geffen-hero.png')`.
- **Decisions:** השתמשנו ב-`@google/generative-ai` SDK ישירות (כבר מותקן ב-node_modules) במקום ל-MCP, כי MCP tools לא היו זמינים כ-deferred tools. המודל שנבחר הוא `gemini-3.1-flash-image-preview` — אותו המודל שיובל השתמש בו בהצלחה בייצור תמונת הסוס.
- **Notes / Caveats:** הקובץ נשמר כ-JPEG אך עם שם geffen-hero.png (mime=image/jpeg) — תואם לדפדפן. אין צורך לתקן את ה-GEMINI_API_KEY — הוא עובד תקין.
- **Related:** [[image-generation]], [[nano-banana-skill-yuval-agent]]

### 2026-05-01 — בניית דף נחיתה Geffen AI [shipped]

- **What was done:** הופעל pipeline מלא של 5 סוכנים. חן חקר את geffen-global.co.il ואסף פרטי קשר (טלפונים, מייל, רשתות חברתיות). יובל נחסם בגלל MCP לא זמין בסוכני-משנה + API key פגום — נוצר רקע CSS Gold במקום תמונה. נכתב קובץ HTML מלא עם Hero, Transformation Selector (3 כרטיסים), Dynamic Roadmap (תוכן שונה לכל בחירה), Contact Form + WhatsApp, Footer. גיא אישר ✅ עם תיקון קל (API חכם).
- **Decisions:** HTML עצמאי עם CDN (לא Next.js project) — מאפשר פתיחה מיידית ללא build. CSS animation במקום Framer Motion כי UMD + Babel Standalone אמין יותר. רקע CSS gradient מדמה "obsidian + liquid gold" עד שה-API key יתוקן.
- **Notes / Caveats:** IMAGE_SLOT מסומן בקוד — להחליף ב-`outputs/geffen-hero.png` כשה-API key תקין. MCP nano-banana-2 עובד רק בסשן ראשי, לא בסוכני-משנה.
- **Related:** [[yael-agent-creation]], [[nano-banana-skill-yuval-agent]], [[image-generation]]
