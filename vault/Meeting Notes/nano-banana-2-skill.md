# nano-banana-2 Skill

## Overview

Skill ליצירת תמונות באמצעות מודל **Google Nano Banana 2** דרך MCP (Model Context Protocol). הוא מוגדר ב-`.Claude/skills/nano-banana-2/SKILL.md` ומספק ממשק אחיד לשליחת prompt ולקבלת תמונה מוחזרת. ה-MCP מוגדר ב-`.claude/settings.json` תחת המפתח `nano-banana-2`. כרגע ה-MCP config הוא placeholder — הפרטים האמיתיים של ה-endpoint טרם הוגדרו.

**קבצים:**
- `.Claude/skills/nano-banana-2/SKILL.md` — הגדרת ה-skill
- `.claude/settings.json` — MCP server config (placeholder)

## Open Questions

- מהם פרטי ה-MCP endpoint האמיתיים של Google Nano Banana 2?
- מה ה-env var הנכון לאימות (GOOGLE_API_KEY / אחר)?
- האם המודל מחזיר URL, base64, או שומר ישירות לקובץ?
- מה פרמטרים נוספים שהמודל תומך בהם (resolution, style, seed)?

## Session Log

### 2026-04-27 — Skill נוצר [wip]

- **What was done:** יצירת `.Claude/skills/nano-banana-2/SKILL.md` עם תיעוד מלא: overview, הוראות שימוש, error handling, ומוסכמת שמות קבצים. יצירת `.claude/settings.json` עם MCP placeholder config.
- **Decisions:** שם ה-MCP tool: `mcp__nano-banana-2__generate_image`. config נשמר ב-project-level settings (לא global) כדי לבודד את ה-MCP לפרויקט הזה בלבד.
- **Notes / Caveats:** ⚠️ ה-MCP config הוא placeholder — חייב להתעדכן עם פרטי endpoint אמיתיים לפני שימוש.
- **Related:** [[yuval-agent]], [[src-skills]]
