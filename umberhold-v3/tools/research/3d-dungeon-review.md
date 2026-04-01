# Review: uheartbeast/3d-dungeon

Source reviewed: `https://github.com/uheartbeast/3d-dungeon`

## Summary

This is a **useful reference prototype** for Umberhold's eventual first-person dungeon exploration layer, but it is **not something I would directly adopt as-is**.

It is best treated as:

- a proof of concept for **step-based 3D grid movement**
- a reference for building a **2D-authored -> 3D-instanced** dungeon pipeline in Godot
- an inspiration source for feel, camera motion, and rendering structure

## What it does well

The project already demonstrates several things Umberhold will need:

1. **First-person step movement**
   - tweened movement between adjacent cells
   - tweened 90-degree rotation
   - simple input-driven blobber navigation feel

2. **Grid-to-3D conversion**
   - a 2D `TileMap` is used as the authored source
   - the runtime instantiates 3D cells from used tiles
   - shared wall faces are removed between adjacent cells

3. **Fast prototype value**
   - very small codebase
   - easy to understand
   - good candidate for a technical spike when validating movement feel

4. **Permissive license**
   - repository license is **MIT**

## Relevant implementation notes

From the reviewed project:

- `World.gd` reads used cells from a 2D tilemap and spawns 3D cell scenes.
- `Cell.gd` removes faces when neighboring cells exist, which is a clean way to avoid drawing hidden interior walls.
- `Player.gd` handles:
  - forward/back/strafe movement via raycasts
  - 90-degree turning via tween
  - step animation timing

## Why it is interesting for Umberhold

Umberhold needs a clear answer to the question:

> How do we author grid maps efficiently while rendering them in first-person 3D?

This repo suggests one workable answer:

- author a dungeon in a **2D grid source**
- convert that source into **3D modular cells**
- keep gameplay logic grid-based even if presentation is fully 3D

That aligns well with the current Umberhold direction in `plan.md` and `gap.md`.

## Why I would not adopt it directly

It falls far short of Umberhold's production needs.

### Missing systems

It does not include Umberhold-specific requirements such as:

- `26x26` canonical map rules
- tile metadata like `texture_id`, triggers, or encounter tables
- transit coordinates between regions
- doors, secrets, locks, and interactables as authored gameplay data
- automap/minimap
- event scripting
- combat transitions
- party state integration
- save/load integration
- multi-floor dungeon content pipeline suitable for a full game

### Engine/runtime mismatch risk

This is a small Godot prototype, not an engine architecture.

Using it wholesale would likely create rework in:

- map schema design
- content pipeline design
- trigger/event systems
- exploration/combat handoff
- UI/HUD integration

### Control mismatch

The prototype includes **strafing**, while Umberhold currently reads more like a classic crawler with deliberate step movement and turning. That is easy to change, but it reinforces that this is a reference, not a drop-in fit.

## Recommendation

**Keep it as a reference implementation, not as an integrated dependency.**

Recommended use order:

1. Use **Gridmapper** for layout drafting.
2. Define the final **Umberhold map schema**.
3. When runtime work starts, build a small **movement/rendering spike** inspired by `3d-dungeon`:
   - 26x26 map loader
   - first-person step movement
   - 90-degree turning
   - modular wall/floor generation
   - basic door/interactable support
4. Only then decide whether any code patterns should be borrowed.

## Best takeaway for Umberhold

The most valuable idea here is not the exact code.

It is the pipeline concept:

**2D authored grid data -> generated modular 3D dungeon presentation**

That is likely the right mental model for Umberhold.
