---
name: elevenlabs-sfx-library
description: Generate, pick and loudness-normalise game sound effects at scale with the ElevenLabs connector, mapped to card and game events. Use for new card sounds or UI cues.
---

# ElevenLabs SFX library

740 cues (690 card + 50 core) were made this way (2026-10-16, 3DTuba PR #24).

## Pipeline (3DTuba scripts)
1. `build_sfx_needs.py`: list needed cues per card (summon, move, attack, hit, ability/spell cast, death/destruction as fits the card) and core events.
2. Generate: ElevenLabs flows of 20 sfx nodes, `generations_count` 3 (a 4th take hits a queue 429). About 12 credits per cue at 3 takes. Never repeat a generation call to retry.
3. Poll `creative_get_flow_run_status`; match generations to cues by prompt text. Status responses carry long signed URLs that expire in about 2 hours, so hand downloading to a subagent.
4. `fetch_takes.py` downloads takes (gitignored), `pick_takes.py` chooses one per cue.
5. `normalize_loudness.py`: EBU R128 per category, -1 dBFS peak cap.
6. Write `assets/audio/sfx/<key>.mp3`, `assets/audio/SFX_MANIFEST.json` and `docs/production/audio/SFX_COVERAGE.md`.

## Brief rules
Short, distinct in a dense tactical mix, no speech unless asked, sci-fi energy textures over medieval ones, mapped to an exact game event. Say in the PR that automatic picks were not listened to, so Matt reviews them.

Runtime wiring of new core cues belongs to Codex's integration lane; leave a README mapping each sound to its event.
