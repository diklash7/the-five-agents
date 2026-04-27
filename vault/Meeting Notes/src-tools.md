# src/tools

## Overview

תיקיית `src/tools/` מכילה פונקציות tool שהסוכנים יכולים לקרוא להן. ב-Anthropic API, tools הן פונקציות חיצוניות שמוגדרות לסוכן ומאפשרות לו לבצע פעולות בעולם האמיתי (חיפוש, כתיבה לקובץ, קריאה ל-API חיצוני, וכו'). כל קובץ בתיקייה מגדיר tool אחת או קבוצת tools קשורות.

**תיקייה:** `src/tools/`
**משויך ל:** כל הסוכנים שזקוקים לאינטראקציה עם מערכות חיצוניות

## Open Questions

- אילו tools יידרשו לחמשת הסוכנים?
- האם ה-tools יהיו משותפות לכל הסוכנים או ייעודיות לכל סוכן?

## Session Log

### 2026-04-27 — Directory created [planned]

- **What was done:** יצירת תיקייה ריקה כחלק מה-scaffold הראשוני.
- **Decisions:** הפרדת tools מ-agents כדי לאפשר שימוש חוזר של tools על-ידי מספר סוכנים.
- **Notes / Caveats:** ריקה לחלוטין — ממתינה להגדרת הסוכנים וצורכיהם.
- **Related:** [[src-agents]], [[src-skills]], [[project-structure]]
