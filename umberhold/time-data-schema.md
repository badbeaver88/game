# Umberhold Time Data Schema

This document defines a small external data model for **world time state**, **day phase calculation**, **service schedules**, and **timed effect durations**.

These schemas are intended to support the approved rules in:
- `umberhold/time-canon.md`
- `umberhold/canon.md`

The machine-readable schema files live in:
- `umberhold/schemas/time/`

Example data files live in:
- `umberhold/examples/time/`

---

## 1. Core Constants

All time systems share these constants:

- **1 step** = **6 seconds**
- **10 steps** = **1 minute**
- **600 steps** = **1 hour**
- **1,800 steps** = **1 day phase**
- **14,400 steps** = **1 day**

These values are repeated in the day-phase schema so tooling can validate and compute against one source of truth.

---

## 2. Day Phase Calculation

The world clock uses a single integer:

- `absolute_step`: total elapsed 6-second steps since the campaign epoch

### Derived values

```text
step_of_day = absolute_step % 14400
day_number = floor(absolute_step / 14400) + 1
phase_index = floor(step_of_day / 1800)
```

`phase_index` maps to the canonical day phases:

0. `dead_of_night`
1. `black_hours`
2. `first_light`
3. `high_morning`
4. `sun_at_zenith`
5. `fading_light`
6. `gloaming`
7. `nightfall`

The player-facing UI should display the phase **name**, not the numeric time.

---

## 3. World Clock State Schema

Schema file:
- `umberhold/schemas/time/world-clock-state.schema.json`

This is the runtime save-state payload for the world clock.

### Required field
- `absolute_step`

### Optional cached fields
These can be recomputed and should be treated as cache only:
- `cached_day_number`
- `cached_step_of_day`
- `cached_phase_id`

### Authoring rule
Store the **minimum necessary state**. If a save system prefers lean data, storing only `absolute_step` is sufficient.

---

## 4. Day Phase Definition Schema

Schema file:
- `umberhold/schemas/time/day-phases.schema.json`

This file defines:
- time constants
- the 8 canonical day phases
- each phase's inclusive start and exclusive end within the day

### Authoring rule
The phases should remain contiguous, non-overlapping, and cover the full day.

---

## 5. Service Schedule Schema

Schema file:
- `umberhold/schemas/time/service-schedules.schema.json`

This schema supports settlement services such as:
- shops
- inns
- taverns
- chantries
- quest boards

### Schedule modes
- `always_open`
- `phase_window`

### `open_phases`
When `schedule_mode` is `phase_window`, the service must declare one or more canonical `open_phases`.

### Current canon guidance
- most shops use:
  - `first_light`
  - `high_morning`
  - `sun_at_zenith`
  - `fading_light`
- inns and taverns use `always_open`

---

## 6. Timed Effect Schema

Schema file:
- `umberhold/schemas/time/timed-effects.schema.json`

This schema is for authored effect definitions that need duration logic.

### Duration modes
- `fixed_steps`
- `combat`
- `turn_boundary`
- `until_saved_or_dispelled`
- `until_dispelled`
- `permanent`

### Use rules

#### `fixed_steps`
Use for world-time durations such as:
- 4-hour buffs
- 8-hour rests
- light sources

#### `combat`
Use for effects that last until combat ends.

#### `turn_boundary`
Use for effects written like:
- until the end of its next turn
- until the start of the caster's next turn

This mode requires:
- `turn_boundary`
- `turns`

#### `until_saved_or_dispelled`
Use for effects such as:
- Beguile
- Blind
- Sleep
- Witchlight

These may still define save timing through `tick_timing` and `removal_triggers`.

---

## 7. Example Mappings

| Existing content | Schema duration |
|---|---|
| Feather Fall (4 hours) | `fixed_steps`, `steps: 2400` |
| Zarveth's Arcane Cloak (4 hours) | `fixed_steps`, `steps: 2400` |
| Shield of Solace (Combat) | `combat` |
| Warden's Mark (Combat) | `combat` |
| Poisoned until end of next turn | `turn_boundary`, `turn_boundary: end_of_target_turn`, `turns: 1` |
| Deathknell fear until end of next turn | `turn_boundary`, `turn_boundary: end_of_target_turn`, `turns: 1` |
| Witchlight until saved or dispelled | `until_saved_or_dispelled` |

---

## 8. Example Files

- `umberhold/examples/time/world-clock-state.example.json`
- `umberhold/examples/time/day-phases.example.json`
- `umberhold/examples/time/service-schedules.example.json`
- `umberhold/examples/time/timed-effects.example.json`

These are examples for tooling and implementation reference, not exhaustive game content.
