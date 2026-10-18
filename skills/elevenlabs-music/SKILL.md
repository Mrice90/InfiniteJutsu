---
name: elevenlabs-music
description: Compose game music (menu theme, faction battle loops, victory and defeat stingers) with the ElevenLabs connector and deliver takes for Matt to choose. Use for soundtrack work.
---

# Game music with ElevenLabs

Done 2026-10-16 (3DTuba PR #25): menu theme, Zeus and Poseidon battle loops, victory and defeat stingers; 20 takes, about 18K credits.

## Steps
1. Write one brief per track: mood, faction identity (Zeus: bright, brass, storm; Poseidon: deep, tidal, synth pads), tempo, length, loopability, instrumental only (confirm no singing).
2. Create one flow, add a music node per track, generate several takes each.
3. Download all takes to project files `music-<date>/` and pick a default per track into `assets/audio/music/`.
4. Loop tracks: trim to a bar boundary and check the seam. Stingers: 2 to 5 s with a clean tail.
5. Log provider, flow id and prompt in the AI disclosure ledger (`docs/production/provenance`) for Steam.
6. Ask Matt to pick final takes; automatic picks are placeholders.
