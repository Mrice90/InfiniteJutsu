---
name: sprint-board-claim
description: Claim, update and release rows on the authoritative local SPRINT_LOG.md board on Matt's laptop without losing edits to other writers. Use before starting or after finishing any task.
---

# Claim work on the sprint board

The top table of `C:\Users\mattj\OneDrive\Documents\AI Dev\Infinite Conquest\SPRINT_LOG.md` is the ownership board. Several AI tools write it at once and overwrite each other within seconds.

## Steps
1. Stage the file with `device_stage_files` and note its `mtimeMs`.
2. Read it; make sure no other member holds an overlapping claim. Respect lanes (ChatGPT rules and card look, Codex integration).
3. Add or edit only your row (status CLAIMED, owner Claude, date, scope, output path). Keep the edit small.
4. Commit with `device_commit_files` and `expectedMtimeMs`. On an mtime rejection, re-stage, re-apply, retry.
5. About 10 seconds later, re-stage and confirm your row is still there; re-apply if it vanished.
6. On delivery, set the row to DELIVERED with the evidence path.

Also keep 3DTuba `PRODUCT_BACKLOG.md` and the local `PRODUCT_BACKLOG.md` in step. Always fetch before writing. New Claude rows used IDs from AI-200 up to avoid clashes.
