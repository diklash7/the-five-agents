# Yuval — Creative Image Agent

## Overview

**יובל** הוא סוכן קריאייטיב ליצירת תמונות עם עקביות ויזואלית. הוא מנתח תמונות מתיקיית `reference/`, מחלץ "Visual DNA" (סגנון, פלטת צבעים, קומפוזיציה, תאורה, מוד), ומשלב אותו עם בקשת המשתמש כדי ליצור prompt מותאם. הוא מפעיל את ה-skill nano-banana-2 דרך MCP ושומר את התוצאה ב-`outputs/`. מוגדר ב-`.Claude/agents/yuval.md`.

**תיקיות:**
- `reference/` — תמונות השראה (ריקה בהתחלה)
- `outputs/` — תמונות מוגמרות

## Open Questions

- מה הפורמט שיובל מקבל בחזרה מ-nano-banana-2 (URL / base64 / path)?
- האם יובל ינתח תמונות reference עם Read tool בלבד, או שיש צורך ב-vision capability?
- האם יובל יעבוד עם batch requests?

## Session Log

### 2026-04-27 — Agent נוצר [wip]

- **What was done:** יצירת `.Claude/agents/yuval.md` עם system prompt מלא: תפקיד, זרימת עבודה 6-שלבית, Visual DNA template, וכללים. יצירת תיקיות `reference/` ו-`outputs/`. עדכון `ceo_agent.md` — הוספת Yuval לרשימת הסוכנים.
- **Decisions:** יובל תמיד מנתח references לפני יצירה (גם אם ריקים). Prompt מוצג למשתמש לפני שליחה. שמות קבצים תיאוריים עם תאריך.
- **Notes / Caveats:** nano-banana-2 MCP עדיין placeholder — יובל לא יוכל לפעול עד שה-MCP יוגדר.
- **Related:** [[nano-banana-2-skill]], [[ceo-agent]], [[src-agents]]
