---
name: kitbash-structures
description: Build low-poly structure models procedurally in headless Blender from a shared kit and palette, without Meshy. Use for structure cards or when Meshy credits are out.
---

# Kitbash structure models

All 34 Zeus and Poseidon structure cards were built this way (2026-10-09, 3DTuba PR #9). Matt approved the style.

## Contract
- One mesh, one material: TokenFactory overwrites every material slot with the folder's `Token` material.
- Colours come from a shared 4x4 palette atlas; collapse each part's UVs onto its palette cell.
- Hex = 2.0 across flats, pointy-top (bmesh hexes match BoardLayout). Structure ≤1.6 tall, ≤1.8 across.
- Follow the faction palette in 3DTuba `docs/production/FACTION_COLOR_GUIDE.md`.

## Steps
1. `kit.py` holds the palette and helpers (columns, domes, pylons, energy coils, hex plinths).
2. Write one builder function per card (`zeus_a.py`, `poseidon_c.py`, ...), reading the card text and art for its silhouette.
3. `build.py` builds all, `verify.py` checks the contract above, `render.py` and `sheet.py` make the review sheet.
4. Stage to `playtest\structure-pilots-<date>\` and a 3DTuba branch with a draft PR. Don't merge before art review.

Known gaps: palette has no brown or pink; models are static (no build-up or collapse animation).
