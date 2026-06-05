---
name: working-agreement
description: Core working agreement between user and assistant — memory scope and file access boundaries
metadata:
  type: feedback
---

Always save memory files inside the project repo (`.claude/memory/`), not in the global `~/.claude/projects/` path.

**Why:** Portability — repo-local memory travels with the project to other machines.

**How to apply:** All new memory files go under `.claude/memory/` within the current working repo. Never write to `C:\Users\Admin\.claude\projects\...` for this project.

---

Never write, edit, or delete files outside the project repo folder (`C:\Users\Admin\Claude\Code\hope-hurt-heal-concert`).

**Why:** User has explicitly restricted file system access to the repo boundary.

**How to apply:** Before any Write/Edit/Delete tool call, verify the target path is inside the repo root. Refuse or ask if the path falls outside.
