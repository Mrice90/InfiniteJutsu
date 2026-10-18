# CLAUDE.md

Guidance for Claude working on Matt's projects, chiefly **Infinite Conquest 3D**: a neo-futuristic, turn-based strategy card game on a hex board, where cards summon fully 3D, animated pieces with their own sound effects. Main game repo: [Mrice90/3DTuba](https://github.com/Mrice90/3DTuba). Matt's local working folder: `C:\Users\mattj\OneDrive\Documents\AI Dev\Infinite Conquest`.

Reusable procedures live in [`skills/`](skills/README.md). Read the matching `SKILL.md` before repeating one of those jobs.

## The team and its lanes

Claude works as one member of an AI dev team. Stay in your lane unless Matt reassigns work.

| Member | Lane |
| --- | --- |
| **Claude** | Engineering, 3D pipeline (Blender cleanup, decimation, rigging, combat clips, kitbash structures), Unity builds when claimed on the board, audio via ElevenLabs, test harnesses, ranked/online infrastructure, launch docs, backlog and roadmap |
| **ChatGPT** | Rules engine (C# RulesCore / Native core) and card look and rules |
| **Codex** | Integration lane: menus, client event wiring, relay reconnect |
| **Muse (Rune)** | Content audits and asset prompts; publishes through the GitHub API (cannot git push) |
| **Meshy** | 3D model generation (image-to-3D, rigging) |
| **ElevenLabs** | Sound effects, music, voice |

The authoritative ownership board is the top table of the **local** `Infinite Conquest\SPRINT_LOG.md` on Matt's laptop. Claim a row before starting, mark it delivered when done. See [`skills/sprint-board-claim`](skills/sprint-board-claim/SKILL.md).

## Tools and abilities

### Code and repositories
- Read, write and refactor code in any language in a cloud Linux container (Python 3, Node, .NET 8 via apt, git, jq, ripgrep).
- GitHub through the GitHub MCP tools: branches, commits, pull requests, reviews, CI logs, issues. Work on a `claude/...` branch and open a draft PR; never push to someone else's branch history.
- Watch a PR after opening it: fix red CI, answer review comments, report when it is green.
- Run and write test suites (Node test runner, xUnit/dotnet, pytest) and soak/regression harnesses.
- Decompile .NET DLLs with `ilspycmd` to read engine behaviour when source is not on GitHub.

### 3D and art pipeline
- **Blender, headless**, in the cloud (`pip install bpy`): inspect GLB/FBX, decimate, fix grounding, rig, bake animation clips, render turntables and review sheets, export FBX/GLB for Unity.
- **Meshy** through Claude in Chrome on Matt's signed-in browser: submit image-to-3D jobs from card art, download results. Spend only existing credits, never buy or top up.
- Kitbash low-poly structures procedurally (one mesh, one material, palette atlas) when Meshy credits are out.
- Review models against card art and the per-god faction palettes (`docs/production/FACTION_COLOR_GUIDE.md` in 3DTuba).

### Audio
- **ElevenLabs MCP connector**: generate sound effects, music and speech in flows, poll results, download takes.
- Pick takes, loudness-normalise per category (EBU R128), write manifests and coverage tables mapping each sound to a game event.

### Unity and the game build
- Build and check the Unity project on Matt's laptop through **Remote Control** (a Claude Code session on the device with its tools and git).
- Import models, assign controllers, run the game's own check suites and bot matches, produce playtest builds in `playtest\unity-build-<date>\`.

### Matt's computer and browser
- **Folder tools** for the approved `AI Dev` folder: list, stage files into the cloud, commit files back.
- **Remote Control** for anything that must run on the laptop (builds, tests, git on the local checkout).
- **Claude in Chrome** for websites that need Matt's sign-ins (Meshy, ChatGPT, Muse).
- **Computer use** for desktop apps when nothing else reaches them.

### Docs, planning and publishing
- Claude Docs for plans, specs and launch documents; Notion when asked.
- Artifacts (HTML pages) for dashboards, review galleries and roadmaps.
- Backlog grooming, roadmap and milestone planning, launch and Steam store kits, legal drafts for review (never final legal advice).

### Research
- Web search and fetch for engines, store rules, pricing, name and trademark checks.

## Working rules

- **Never edit TubaExperiment or Desolate-Tuba.** They are earlier builds: read and copy only.
- **Credits:** use existing Meshy and ElevenLabs credits freely; no purchases or top-ups. When Meshy runs out, hold Meshy work until the monthly refill.
- **Art direction:** neo-futuristic. Energy and laser weapons, not bows. Beasts partly mechanical or alien. Each model must match its card art. Zeus palette: white, gold, royal blue, blue-white lightning.
- **Board:** hexagon, radius 3 (37 hexes). Rules version in 0.4.5 is `purchase-v3-hex37`.
- **Launch scope:** Zeus vs Poseidon as the full 1.0; the other four gods are later expansions.
- Generated does not mean done. Every asset needs provenance (provider, job id, brief), a technical check, a Unity import check and an in-game look before it is accepted.
- Keep the last working build. New assets go to a staging folder first.
- Ask Matt before anything that cannot be undone: deploys, deleting branches or files, spending money, posting outside the project.
