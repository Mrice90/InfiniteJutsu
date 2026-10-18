---
name: glb-decimate
description: Slim heavy Meshy GLB models to a triangle budget (30K) without losing their silhouette, with before/after review renders. Use when in-game models are too heavy.
---

# Decimate GLB models to a budget

Used for the 12 batch-07 Poseidon models (2026-10-15): 60K+ down to 30K, min silhouette IoU 0.972. Matt approved the result.

## Steps
1. Set up Blender per [blender-headless-cloud](../blender-headless-cloud/SKILL.md). Stage source GLBs from the laptop.
2. For each model: import, join meshes, apply a Decimate (collapse) modifier with ratio = budget / current tris. Keep UVs and the original textures (BaseColor, MetallicRoughness, Normal).
3. Measure silhouette loss: render front, 3/4, side and top masks before and after, compute IoU per view. Flag any view under 0.97 and re-run with planar pre-pass or a higher budget.
4. Render a before/after detail sheet per model for review.
5. Export `<card>_30k.glb`, `.fbx`, `.blend`, plus `<card>_report.json` (tris before/after, IoU per view, height).
6. Commit sheets, reports and scripts to a 3DTuba branch; models go to project files and the laptop's `playtest\decimate-<batch>-<date>\` (too big for git).

## Notes
- The decimation FBX is not game-ready (wrong height, stray camera). Build the game token from the 30K GLB with 3DTuba's `docs/production/tools/glb_to_token_fbx.py`.
- In-game tokens were already ~60K, so measure the real in-match saving against those, not the raw Meshy files.
