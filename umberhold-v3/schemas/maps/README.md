# Umberhold Grid Map Schema

This document defines the first draft of a machine-readable schema for Umberhold's **26x26 exploration maps**.

These schemas are intended to support the approved direction in:

- `DESIGN.md`
- `plan.md`
- `gap.md`

The machine-readable schema file lives in:

- `schemas/maps/grid-map.schema.json`

Example data files live in:

- `examples/maps/`

---

## 1. Scope

One map file represents **one explorable 26x26 floor or region layer**.

Examples:

- Umberhold village surface
- Gravenhollow Manor floor 1
- East Graveyard crypt level
- wilderness region layer

This schema is for **exploration-space authoring**, not combat arenas.

---

## 2. Core authoring model

The schema splits map data into five concerns:

1. **Map metadata**
   - ids
   - map type
   - region ownership
   - floor index

2. **Tile data**
   - exactly one tile record for every coordinate from `A1` through `Z26`
   - wall/walkable state
   - texture overrides
   - height / ceiling data
   - encounter and trigger references

3. **Edge data**
   - doors
   - secret doors
   - portcullises
   - illusion walls
   - other boundary features between tiles

4. **Placed props**
   - chests
   - stairs
   - ladders
   - altars
   - switches
   - decorative or blocking set dressing

5. **Trigger and transit metadata**
   - step/on-enter events
   - fire policy
   - flag requirements
   - links to other maps

---

## 3. Coordinate rules

The canonical coordinate system is:

- columns: `A` through `Z`
- rows: `1` through `26`
- origin: `A1`
- `A1` is the **top-left** tile
- increasing letters move **east/right**
- increasing numbers move **south/down**

Each map file must define **all 676 coordinates**.

---

## 4. Tile rules

The `tiles` object is the canonical source of per-coordinate gameplay state.

Minimum expected usage:

- `is_wall`
- optional texture overrides
- tags
- encounter overrides
- step trigger references
- interactable reference when needed

### Recommended interpretation

- `is_wall: true` = solid, non-walkable tile
- `is_wall: false` = walkable or otherwise occupiable tile
- hazards such as pits, lava, shallow water, or cursed ground should usually be represented as:
  - `is_wall: false`
  - `tags` describing the hazard
  - optional trigger / interaction metadata

---

## 5. Doors and secret doors

Doors are **not** stored by turning destination tiles into a special tile type.

Instead, they live in the `edges` array as boundary features attached to:

- a source coordinate
- one of the four cardinal sides

This makes it explicit that doors, secret doors, and similar features exist **between** tiles.

### Authoring rule

For any shared boundary, author the feature **once**.

Example:

- if a door exists between `H6` and `I6`, store one edge anchored at:
  - `at: "H6"`
  - `side: "east"`

Do not author the same door again from `I6` west.

---

## 6. Props vs interactions

Use `props` for placed objects that exist on a tile, such as:

- stairs
- chests
- levers
- wells
- statues
- ladders
- signs

If the prop has gameplay logic, attach an `interact_id`.

Use plain tile metadata only when no distinct placed object is needed.

---

## 7. Trigger policy

Tiles reference trigger instances by id through `step_trigger_ids`.
Trigger definitions live in the map file's `triggers` array.

This solves an important production question from `gap.md`:

- whether events fire once, always, or conditionally

Current draft fire policies are:

- `always`
- `once_per_save`
- `once_per_campaign`
- `once_when_enabled`

---

## 8. Transit links

Map-to-map movement is authored in `transits`.

Each transit declares:

- source coordinate
- travel mode
- destination map id
- destination entry point id
- optional flag gating

Destination arrival positions are authored in `entry_points`.

This keeps region/floor linking explicit and avoids brittle hardcoded coordinate jumps.

---

## 9. Defaults

The `defaults` block exists to reduce repetition across 676 tiles.

Use it for common values such as:

- wall texture set
- floor texture set
- ceiling texture set
- ceiling height
- default random encounter table
- baseline tags

Per-tile values override the defaults.

---

## 10. Validation limits

This schema validates structure, but some design rules still require higher-level validation tooling.

Examples of rules that should be checked by a validator or importer:

- edge features do not duplicate the same boundary twice
- transits point to valid destination maps/entry points
- trigger ids referenced by tiles actually exist
- every walkable stair tile has a matching transit or interaction
- secret areas remain reachable by intended mechanics

---

## 11. Example file

See:

- `examples/maps/gravenhollow-manor-floor-1.example.json`

This example is intentionally small in gameplay scope but complete in structure.
