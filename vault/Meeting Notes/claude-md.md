# CLAUDE.md

## Overview

`CLAUDE.md` הוא קובץ ההנחיות הראשי ל-Claude Code במאגר זה. הוא ממוקם בשורש הפרויקט ונטען אוטומטית על-ידי Claude Code לפני כל משימה. הקובץ מתעד את מבנה הפרויקט, הארכיטקטורה, ומשתני הסביבה הנדרשים. **כולל כעת הוראה מפורשת להפעיל תמיד את CEO Agent כנקודת כניסה ראשונה לכל משימה.**

**קובץ:** `CLAUDE.md` (שורש הפרויקט)
**משויך ל:** כל המפתחים ועוזרי ה-AI בפרויקט

## Open Questions

- יש להוסיף פקודות build/lint/test ברגע שהשפה תיבחר
- לעדכן את ה-Architecture diagram כשיוגדרו 4 הסוכנים הכפופים

## Session Log

### 2026-04-27 — Initial CLAUDE.md created [wip]

- **What was done:** יצירת CLAUDE.md עם סקירת פרויקט, מבנה תיקיות, ופלייסהולדר ל-ANTHROPIC_API_KEY.
- **Decisions:** נשאר מינימלי בכוונה — תוכן מוקדם מדי מתיישן. סעיף הארכיטקטורה נדחה לסשן בו הסוכנים יוגדרו.
- **Notes / Caveats:** חייב להתעדכן בחירת שפה ועם התקדמות הפיתוח.
- **Related:** [[project-structure]], [[obsidian-vault-workflow-skill]]

### 2026-04-27 — CEO Agent הוסף כנקודת כניסה חובה [wip]

- **What was done:** הוספת סעיף "CEO Agent — Single Entry Point" ל-CLAUDE.md עם הוראה מפורשת: לכל משימה יש להפעיל תחילה את CEO Agent. נוסף diagram של ארכיטקטורת ה-orchestrator.
- **Decisions:** המנכ"ל הוא נקודת הכניסה היחידה — אסור לקרוא לסוכן כפוף ישירות. זה אוכף את ארכיטקטורת ה-orchestrator בכל מצב.
- **Notes / Caveats:** ה-diagram יתעדכן כש-4 הסוכנים יוגדרו.
- **Related:** [[ceo-agent]], [[src-agents]]
