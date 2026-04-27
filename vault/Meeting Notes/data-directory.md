# data/

## Overview

תיקיית `data/` מכילה קבצי קלט ופלט לריצות הסוכנים. היא מבודדת נתונים מהקוד, כך שניתן לשנות inputs/outputs ללא נגיעה בלוגיקה. מתאימה לדוגמאות, תבניות, תוצאות ריצה, ו-fixtures לבדיקות.

**תיקייה:** `data/`
**משויך ל:** כל הסוכנים — קלט לעיבוד ופלט לשמירה

## Open Questions

- האם data/ תכנס ל-.gitignore (בגלל נתונים רגישים/גדולים)?
- מה פורמט הנתונים — JSON, CSV, טקסט חופשי?

## Session Log

### 2026-04-27 — Directory created [planned]

- **What was done:** יצירת תיקייה ריקה כחלק מה-scaffold הראשוני.
- **Decisions:** הפרדת data מ-src מונעת ערבוב בין קוד לנתונים ומפשטת .gitignore.
- **Notes / Caveats:** ריקה לחלוטין — שקול להוסיף ל-.gitignore אם יכיל נתונים רגישים.
- **Related:** [[project-structure]], [[src-agents]]
