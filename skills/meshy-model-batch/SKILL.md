---
name: meshy-model-batch
description: Generate a batch of 3D unit models in Meshy from card art through Claude in Chrome, then stage and review them. Use when new card models are needed and credits remain.
---

# Meshy model batch

## Before starting
- Check the Meshy credit balance on the site. Cheapest job: Meshy 6 Lite image-to-3D, 10 credits; 7.1 is 25. Never buy credits. If the balance can't cover the batch, stop and hold until the monthly refill.
- Another session may also use the account; re-check the balance before each submit to avoid double-spend.
- Prioritise from 3DTuba `docs/reviews/2026-10-08-asset-library-gaps.csv`.

## Brief (per 3DTuba `docs/production/ASSET_PIPELINE.md`)
Subject, silhouette, neo-futuristic style (energy weapons, part-mechanical beasts), scale, topology/material targets, pose, formats (GLB), and prohibited traits. Use the card's own art as the image input; the model must match it. Use the god's three-colour palette.

## Steps
1. Load Claude in Chrome tools in one ToolSearch call, open a new tab on Meshy (Matt is signed in).
2. Submit one representative model first and review it before the rest of the batch.
3. Record provider job id, brief, credits spent and output path for every job. Never resubmit an uncertain paid job.
4. Download GLBs into `3DTuba\assets\staging\meshy\batch-<nn>\`.
5. Check each with `docs/production/tools/check_glb.py` (tris, bounds, textures), render a review sheet, compare to card art.
6. Heavy models go through [glb-decimate](../glb-decimate/SKILL.md); characters through [rig-combat-clips](../rig-combat-clips/SKILL.md).
