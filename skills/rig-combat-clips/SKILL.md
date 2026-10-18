---
name: rig-combat-clips
description: Rig posed Meshy statue models without Meshy and bake six grounded combat clips (idle, walk, attack, hit, death, summon) for Unity. Use when characters need animation.
---

# Rig characters and bake combat clips

Done for all 48 Zeus and Poseidon characters (2026-10-16, 3DTuba PR #26, scripts in `docs/production/rig-roster/2026-10-15/scripts`). No Meshy credits used.

## Steps
1. Blender setup per [blender-headless-cloud](../blender-headless-cloud/SKILL.md).
2. Run `probe.py` to render gridded views of each model, then hand-place joints in `cfg/<card>.json`. Meshy batch-07 models are posed statues, so auto-fit fails.
   - Humanoids: Chest is a joint, not a bone; props riding the torso name bone `Spine2`; A-pose statues use `arm_down`.
   - Seated, flying, mounted and machine units use `kind: creature` (body/spine/tail/limbs; wings as fin limbs, riders as Spine1 boxes).
   - Thrones and plinths: `anchored: true` (hips rotate only) and `death_topple` to shrink the fall.
   - Probe grid spacing varies per model; check every cfg with `overlay.py` before rigging.
3. `rig_posed.py`: bone heat weights. If heat fails on a Meshy mesh, solve on a voxel proxy at 10x scale keeping only the largest island. Base and weapon verts are `rigid`.
4. Bake Idle, Walk, Attack, Hit, Death, Summon with events `impact`, `down`, `land`. Mute other NLA tracks while baking, or earlier clips leak into the ground solve.
5. Run `actz.py` to check each action alone stays on the ground (it matches Unity's numbers). Fix any sink or float before staging.
6. Render animated previews, export FBX, stage to `playtest\rig-combat-<date>\models`.

## Unity hookup
- 0.4.5's `PresentationMotion.PlayRig` already fires Animator triggers `Move/Attack/Summon/Destroy/Ability/Hit` when a token has an Animator with a controller.
- Tokens load via `Resources.Load(card.model)` from `Playtest/Resources/Tokens/<card>/<card>.fbx`; import as Generic and assign a controller in TokenFactory.
- Rigged models face 0° yaw like the old tokens; TokenFactory rescales and recentres by bounds.

## Gotchas
- Batch list files need a trailing newline or two cards merge.
- Blender FBX re-import connects Hips to Root and drops Hips translation; Unity is unaffected.
- Remove vertex groups by collecting ids first, never while iterating `v.groups`.
