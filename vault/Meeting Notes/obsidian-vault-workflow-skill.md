# Obsidian Vault Workflow Skill

## Overview

Skill מותאם אישית של Claude Code הממוקם ב-`.Claude/skills/obsidian-vault-workflow/SKILL.md`. הוא אוכף פרוטוקול חובה של קריאה/כתיבה ל-vault לפני ואחרי כל משימה. Phase 1 (לפני): זיהוי נושא, איתור קובץ נושא, קריאת הקשר אחרון. Phase 2 (אחרי): הוספת רשומת session log מתאורת ל-vault. ה-Skill הוא שכבת הזיכרון ארוך הטווח של הפרויקט, משלים את CLAUDE.md.

**קובץ:** `.Claude/skills/obsidian-vault-workflow/SKILL.md`
**משויך ל:** Claude Code (מופעל בידי המפתח בתחילת ובסוף כל משימה)

## Open Questions

- none

## Session Log

### 2026-04-27 — Skill identified and vault initialized [shipped]

- **What was done:** קריאת SKILL.md במלואו. אתחול מבנה vault/ (Meeting Notes, Content Briefs, Publishing Log, Brand Guidelines) ויצירת topic files לכל קבצי הפרויקט הקיימים.
- **Decisions:** השימוש ב-`vault/Meeting Notes/` לכל הנושאים הנוכחיים כיוון שכל העבודה עד כה היא ארכיטקטורה/קוד. שאר התיקיות נשארות עם stub של index.
- **Notes / Caveats:** ה-Skill חייב להיות מופעל בתחילת ובסוף כל משימה — הוא אינו אוטומטי.
- **Related:** [[project-structure]], [[claude-md]]
