# src/agents

## Overview

תיקיית `src/agents/` מכילה את הגדרות הסוכנים של הפרויקט — כל קובץ מגדיר סוכן אחד. כל סוכן הוא יחידה עצמאית בעלת תפקיד ספציפי, ומשתמש ב-Anthropic Claude API כ-engine. זהו ליבת הפרויקט — הסוכנים הם הישויות שמבצעות את הלוגיקה העסקית.

**תיקייה:** `src/agents/`
**משויך ל:** לב הפרויקט — כל סוכן מהחמישה יתגורר כאן

## Open Questions

- מהם שמות 4 הסוכנים הכפופים ותפקידיהם?
- מה מחלקת הבסיס / interface המשותפת לכל סוכן?

## Session Log

### 2026-04-27 — Directory created [planned]

- **What was done:** יצירת תיקייה ריקה כחלק מה-scaffold הראשוני.
- **Decisions:** תיקייה ייעודית לסוכנים בלבד — tools ו-skills בתיקיות נפרדות.
- **Notes / Caveats:** ריקה לחלוטין — ממתינה לבחירת שפה ולהגדרת חמשת הסוכנים.
- **Related:** [[project-structure]], [[src-tools]], [[src-skills]]

### 2026-04-27 — CEO Agent מוגדר [wip]

- **What was done:** הוגדר סוכן המנכ"ל כ-orchestrator ראשי. נכתב PRD מלא (`docs/PRD-ceo-agent.md`) ו-`.Claude/agents/ceo_agent.md`. הסוכן ינהל 4 סוכנים כפופים — הזהות שלהם תיקבע בהמשך.
- **Decisions:** הסוכנים מתקשרים דרך orchestrator (לא ישירות). הניתוב מבוסס LLM reasoning. תקשורת עם המשתמש בזמן אמת.
- **Notes / Caveats:** 4 slots לסוכנים עדיין ריקים. שפה לא נבחרה סופית.
- **Related:** [[ceo-agent]], [[project-structure]], [[src-utils]]
