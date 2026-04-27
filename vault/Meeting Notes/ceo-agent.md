# Ohad — CEO Agent

## Overview

**אוהד** הוא הסוכן הראשי (CEO Agent) ו-orchestrator המרכזי של מערכת The Five Agents. הוא נקודת הכניסה היחידה למשתמש — קולט משימת מחקר/אנליזה בשפה טבעית, מחליט בעצמו (LLM reasoning) אילו מ-4 הסוכנים הכפופים לו להפעיל ובאיזה סדר (sequential/parallel), ומדווח למשתמש בזמן אמת לאחר כל שלב. הגדרתו כ-Claude Code sub-agent נמצאת ב-`.Claude/agents/ceo_agent.md`. ה-PRD המלא נמצא ב-`docs/PRD-ceo-agent.md`.

**קבצים:**
- `.Claude/agents/ceo_agent.md` — הגדרת הסוכן ל-Claude Code
- `docs/PRD-ceo-agent.md` — מסמך דרישות מלא

## Open Questions

- מהם 4 הסוכנים הכפופים ותפקידיהם?
- האם לשמור execution plans ב-`data/` לצורך debugging?
- מהו מספר הסוכנים המקסימלי שיכולים לרוץ במקביל?
- האם המנכ"ל יהיה stateful (זיכרון בין משימות) או stateless?
- שפה סופית: Python או TypeScript?

## Session Log

### 2026-04-27 — PRD ו-agent.md נוצרו [wip]

- **What was done:** כתיבת PRD מלא (`docs/PRD-ceo-agent.md`) עם 10 סעיפים: Overview, Goals, User Story, I/O, Decision Logic, Sub-Agent Contract, Reporting, Error Handling, Spec, Open Questions. כתיבת `.Claude/agents/ceo_agent.md` עם frontmatter ו-system prompt מלא.
- **Decisions:** ניתוב מבוסס LLM reasoning בלבד (לא כללים קבועים). דיווח בזמן אמת חובה. 4 slots לסוכנים — ייוגדרו בהמשך. CLAUDE.md יפנה למנכ"ל כנקודת כניסה יחידה.
- **Notes / Caveats:** שפה לא נבחרה — ה-interface contract מוצג בשתי שפות (Python/TS). 4 הסוכנים עדיין ריקים.
- **Related:** [[project-structure]], [[src-agents]], [[claude-md]]

### 2026-04-27 — שם המנכ"ל נקבע: אוהד [wip]

- **What was done:** עדכון שם הסוכן ל-"אוהד" בכל הקבצים: `ceo_agent.md`, `PRD-ceo-agent.md`, `CLAUDE.md`, ו-vault.
- **Decisions:** השם אוהד ישמש בכל הפניות לסוכן — ב-description, ב-system prompt, וב-CLAUDE.md.
- **Notes / Caveats:** שם הקובץ נשאר `ceo_agent.md` — רק השם המוצג השתנה.
- **Related:** [[claude-md]], [[src-agents]]
