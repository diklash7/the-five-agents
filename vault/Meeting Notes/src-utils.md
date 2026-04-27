# src/utils

## Overview

תיקיית `src/utils/` מכילה utilities משותפים לכל הפרויקט — לקוח ה-Anthropic API, פונקציות עזר, קונפיגורציה, ו-helpers שאינם שייכים לסוכן ספציפי. זהו הקוד התשתיתי שכל חלקי הפרויקט יכולים לייבא.

**תיקייה:** `src/utils/`
**משויך ל:** כל חלקי הפרויקט — agents, tools, ו-skills

## Open Questions

- מה יהיה מבנה לקוח ה-Anthropic API (singleton? factory?)?
- האם יהיה כאן ניהול של logging ו-error handling מרכזי?

## Session Log

### 2026-04-27 — Directory created [planned]

- **What was done:** יצירת תיקייה ריקה כחלק מה-scaffold הראשוני.
- **Decisions:** ריכוז קוד תשתיתי משותף במקום אחד מונע כפילות בין הסוכנים.
- **Notes / Caveats:** ריקה לחלוטין — יאוכלס כשתיבחר שפה וייבנה לקוח ה-API.
- **Related:** [[src-agents]], [[src-tools]], [[src-skills]], [[project-structure]]
