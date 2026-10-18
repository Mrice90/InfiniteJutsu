---
name: unity-build-remote
description: Build, check and package a Unity playtest build of Infinite Conquest on Matt's laptop through Remote Control. Use for any Unity import, build or in-game check.
---

# Unity playtest build on the laptop

Matt allows Claude to work on the Unity build directly when the task is claimed on the board.

## Steps
1. Claim the row in the local `SPRINT_LOG.md` ([sprint-board-claim](../sprint-board-claim/SKILL.md)).
2. `list_devices`, then `start_rc_session` on the approved `AI Dev` folder with a precise brief: source project, what to change, which checks to run, where to put the build.
3. Copy the last working project to a new working folder; never build in place over the release candidate. Skip only the top-level `Build` folder when copying (not `Packages/*/Build`).
4. Import assets: models into `Resources/Tokens/<card>/<card>.fbx` with `Token.mat`; Generic rig plus controller for animated units.
5. Run the project's own check suites and a set of bot matches. Confirm the rules DLLs are byte-identical to the release (SHA256SUMS) unless the task is a rules change.
6. Build to `Infinite Conquest\playtest\unity-build-<name>-<date>\` and write evidence to `reviews\<name>-<date>\DELIVERY.md` (what changed, suite results, screenshots).
7. Mark the board row delivered and ask Matt for a hands-on look.

## Notes
- Folder tools are withheld while an RC session runs from the same thread; stop the session to get them back.
- Remote Control can git push from the laptop checkout.
- Rules engine changes belong to ChatGPT; integration wiring to Codex.
