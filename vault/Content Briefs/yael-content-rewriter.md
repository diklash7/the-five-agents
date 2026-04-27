# Yael — Content Rewriter Agent

## Overview

**יעל** היא סוכנת כתיבה ועריכה. היא מקבלת מאמרים גולמיים מתיקיית `Content/`, מיישמת את סגנון הכתיבה של המותג (professional with personality — human, direct, short sentences, strong hook), ושומרת את הפלט ב-`Output/`. לאחר הכתיבה היא מעבירה את קובץ המקור ל-`Content/Ready/`. אם דרוש ויזואל, יעל מאצילה ליובל ליצירת תמונה. מוגדרת כ-system prompt ישירות בתוך השיחה (לא ב-.Claude/agents/).

## Open Questions

- האם יעל צריכה להיות מוגדרת גם ב-`.Claude/agents/yael.md` לשימוש עתידי?
- כיצד יעל אמורה לעבוד כשאין קבצים ב-`Content/` (graceful exit)?

## Session Log

### 2026-04-27 — First article rewrite: ai-agents-intro [shipped]

- **What was done:** קריאת `Content/ai-agents-intro.md` (אנגלית, ~200 מילה). כתיבה מחדש לפי סגנון המותג: hook חזק, מבנה נושאי ברור, משפטים קצרים-בינוניים, קול ישיר, קצה אקציונבלי. לא נדרשה תמונה. שמירה ל-`Output/ai-agents-intro.md`. ארכיב ל-`Content/Ready/`.
- **Decisions:** לא הופעל יובל — המאמר טקסטואלי לחלוטין ותמונה לא הוסיפה ערך משמעותי. השפה זוהתה כאנגלית והפלט נכתב באנגלית (כלל: שפת המקור = שפת הפלט).
- **Notes / Caveats:** המקור היה קצר מאד ועם משפטים כבדים מאד. הפלט כמעט פי שניים באורך — תוצר של הוספת סאב-כותרות ומבנה, לא פיברוק עובדות.
- **Related:** [[yuval-agent]], [[project-structure]]
