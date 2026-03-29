# Umberhold Time Canon

This document captures the current approved rules for **world time, day phases, and service availability**.

It is intended to align exploration, combat duration tracking, spell timers, status effects, and settlement schedules under one shared model.

---

## 1. Core Time Model

Umberhold uses a **discrete, action-driven time system**.

Time is **not** tied to real-world seconds and does **not** advance passively.

### Core Unit
One time step equals **6 seconds** of in-game time.

### Approved 6-Second Costs
The following currently advance time by one step:
- one **successful grid movement** into a new tile
- one **full combat round** in which all combatants complete their turns

### Conversion Rules
- **10** time steps = **1 minute**
- **600** time steps = **1 hour**
- **14,400** time steps = **1 full day**

### Terminology Note
The combat canon uses **turn** to mean an individual combatant's activation.

For timekeeping purposes, the approved **6-second** combat unit is the **full round**, not a single combatant turn.

This keeps the time rules consistent with the existing combat-turn structure.

---

## 2. No Passive Time

Time advances only when the player performs an action with a defined time cost.

### Rules
- if the player stops moving or acting, **time stops**
- menus and indecision do **not** advance time
- the world remains static until the player acts again
- no pause function is required for world simulation

This means Umberhold has **no real-time pressure**, even though it still tracks an internal world clock.

---

## 3. Time of Day Presentation

The game tracks the exact in-world time internally, but does **not** show exact hours to the player.

### Player-Facing Display Rule
The UI shows only the **current phase of the day**.

This phase name is displayed **below the minimap**.

The exact clock time remains hidden.

---

## 4. Day Phases

Each day is divided into **8 named phases**.

Each phase lasts **3 hours**.

| Phase | Internal Time Range |
|---|---|
| Dead of Night | 12am-3am |
| Black Hours | 3am-6am |
| First Light | 6am-9am |
| High Morning | 9am-12pm |
| Sun at Zenith | 12pm-3pm |
| Fading Light | 3pm-6pm |
| Gloaming | 6pm-9pm |
| Nightfall | 9pm-12am |

Only the **phase name** is surfaced to the player.

---

## 5. What Time Affects

All timed systems use this same underlying clock.

This includes:
- **spell durations**
- **status effects**
- **world interactions**
- **service availability**

This allows combat, exploration, and settlement logic to share one consistent duration model.

---

## 6. Shops and Service Availability

Settlements may gate services by day phase.

### Normal Shop Hours
Most shops and daylight-facing services operate during:
- **First Light**
- **High Morning**
- **Sun at Zenith**
- **Fading Light**

This includes typical shops such as:
- equipment merchants
- general goods vendors
- alchemists
- identification services

### Always Open
The following remain available at all hours:
- **inns**
- **taverns**

### Other Services
Any service not explicitly covered above may define its own hours later if needed.

---

## 7. Implementation Guidance

Internally, all time-tracked systems should resolve against the same **6-second step counter**.

Examples:
- a **4-hour** effect lasts **2,400** time steps
- a **hooded lantern** lasts **4 hours = 2,400** time steps
- a **torch** lasts **1 hour = 600** time steps
- an **8-hour Rest** lasts **4,800** time steps
- a **3-hour day phase** lasts **1,800** time steps

Settlement services should be authorable with explicit allowed day phases rather than bespoke per-scene logic.

Implementation references:
- `umberhold/time-data-schema.md`
- `umberhold/schemas/time/world-clock-state.schema.json`
- `umberhold/schemas/time/day-phases.schema.json`
- `umberhold/schemas/time/service-schedules.schema.json`
- `umberhold/schemas/time/timed-effects.schema.json`
- `umberhold/examples/time/`

---

## 8. Status

This category is **approved canon** for the current design direction.
