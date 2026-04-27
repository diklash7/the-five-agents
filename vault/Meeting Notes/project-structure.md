# Project Structure

## Overview

The Five Agents הוא פרויקט masterclass המדגים ארכיטקטורת multi-agent באמצעות Anthropic Claude API. הפרויקט מאורגן תחת ספריית `src/` עם הפרדה ברורה בין agents, tools, skills, ו-utils. נתוני קלט/פלט מבודדים ב-`data/`. ה-vault הנוכחי משמש כזיכרון ארוך טווח של הפרויקט. השפה ו-framework עדיין לא נבחרו.

## Open Questions

- איזו שפה תשמש — Python או TypeScript?
- מהם חמשת הסוכנים ואיך הם מתקשרים?
- מה מנגנון התקשורת בין הסוכנים (event-driven, orchestrator, pipeline)?
- האם תיקיית `outputs/` תיכנס ל-.gitignore (כרגע כן — שנה אם רוצים לעקוב אחרי תמונות).

## Session Log

### 2026-04-27 — Initial project scaffold [wip]

- **What was done:** יצירת מבנה תיקיות ראשוני (src/agents, src/tools, src/skills, src/utils, data/), CLAUDE.md, ודחיפה ל-GitHub. אתחול vault.
- **Decisions:** הפרדה בין agents/tools/skills/utils כדי לאכוף אחריות יחידה למודול. data/ מבודד קלט/פלט מהקוד.
- **Notes / Caveats:** כל התיקיות ריקות. תיקיות ריקות לא נעקבות ב-git ללא קבצי .gitkeep.
- **Related:** [[claude-md]], [[src-agents]], [[src-tools]], [[src-skills]], [[src-utils]], [[data-directory]]
