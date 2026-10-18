---
name: blender-headless-cloud
description: Set up and run Blender headless (bpy) in a cloud container to inspect, fix, render or export game models. Use before any Blender job in the cloud.
---

# Blender headless in the cloud

## Setup
```bash
python3 -m pip install bpy==5.2.2
apt-get install -y libegl1 libegl-mesa0 libgl1-mesa-dri   # needed for Workbench/EEVEE renders
```

## Run scripts
- Always run as `python3 -I script.py`. Plain `python3` can crash with a glog double-init error, and a scratch file named like a stdlib module (`inspect.py`, `json.py`) shadows it and breaks bpy.
- Keep scripts in their own folder, separate from downloaded models.

## Moving files to and from Matt's laptop
- Stage inputs with the device folder tools (`device_stage_files`); they land in `/mnt/user-data/uploads/<folder>/`.
- Paths more than about 7 folders deep under `AI Dev` (Unity `Resources/Tokens`) can't be staged; use the `3DTuba\assets\staging` copies.
- Write results under `/mnt/project-files/<task>-<date>/` and `device_commit_files` them to `Infinite Conquest\playtest\<task>-<date>\`. Files over 25 MB (.blend) won't commit; ship FBX/GLB instead.

## Export gotchas
- glTF-imported textures export into FBX with extensionless names, so Unity makes no textures. Rename images to `.jpg`/`.png` before FBX export, or hand Unity the GLB.
- Remove stray cameras, lights and icospheres before export.
- Report triangle count, height, bounds and origin for every export.

Related: [glb-decimate](../glb-decimate/SKILL.md), [rig-combat-clips](../rig-combat-clips/SKILL.md).
