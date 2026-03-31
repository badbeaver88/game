# Monsters Meta

Extracted from the master design document (see `DESIGN.md`).

## Summary
`DESIGN.md` defines the **monster combat framework** well, but it does **not** yet contain a true monster roster.

You have:
- enemy slot rules
- melee vs ranged AI concepts
- random vs fixed encounter structure
- sub-boss / boss hierarchy

You do **not** yet have:
- named starter monsters with full data
- stat blocks
- loot tables
- encounter-group compositions
- visual identity lists

---

## Monster Framework Already Present

### Combat/AI rules already defined
- Enemy Front Rank = 6 slots
- Enemy Rear Rank = 6 slots
- Sizes:
  - Medium = 1 slot
  - Large = 2 slots
  - Huge = 3 slots
  - Gigantic = 4 slots
- Melee enemies advance into front rank
- Ranged/caster enemies prefer rear rank
- Random encounters exist
- Fixed set-piece encounters exist
- Bosses and sub-bosses exist conceptually

### Named monster references found in `DESIGN.md`
These are references, not full entries:
- Lich King
- Ogre
- generic poisonous creature
- generic archers/casters
- generic undead / silent dead themes

This means the **framework exists, but the content roster does not**.

---

## What Still Needs To Be Authored

### Core starter roster for the Manor / early game
You need a real opening monster set, likely including things like:
- shambling undead
- graveyard beasts
- cult retainers
- necromantic servants
- manor guardians
- one or two ranged/caster threats

### Per-monster data still needed
For each monster, you still need:
- name
- short lore/description
- size / slot usage
- rank preference
- AI profile
- range value
- stats
- AC / HP / attacks
- damage values
- resistances / immunities if any
- XP value
- loot table
- portrait/visual brief
- sound / FX identity if desired

### Encounter composition still needed
You also need:
- random encounter tables
- fixed encounter groups
- boss entourage compositions
- per-region roster lists

---

## Minimum Monster Buckets You Need

### 1. Basic Melee Trash Enemies
For front-rank pressure.

### 2. Rear-Rank Threats
Archers, acolytes, shamans, hexers, or necromancers.

### 3. Durable Brutes
Large/Huge enemies that teach the slot system.

### 4. Utility/Status Enemies
Enemies that poison, blind, frighten, charm, or debuff.

### 5. Mini-Bosses
Unique enemies with recognizable gimmicks.

### 6. Big Bosses
Gigantic or otherwise signature encounters with story significance.

---

## Monster Gaps Checklist

- [ ] Build the first true monster roster for the Manor
- [ ] Define a monster data schema
- [ ] Define starter random encounter tables
- [ ] Define starter fixed encounters
- [ ] Define mini-boss and boss stats
- [ ] Define loot drops by monster/group
- [ ] Define monster portraits/visual themes
- [ ] Define undead traits and resistances if used heavily
- [ ] Define ranged/caster AI profiles in data terms
- [ ] Define poison-capable creatures for Shadowman harvesting loops

---

## Suggested Minimum Vertical Slice Roster Size

For Umberhold + the Manor, aim for at least:
- 4-6 common monsters
- 2-3 elite/special monsters
- 1 mini-boss
- 1 main boss

That is the minimum needed to make the dungeon feel like a real place rather than a test arena.

---

## Status
This is one of the **largest missing content categories** in `DESIGN.md`.
The rules for monsters are there.
The monsters themselves mostly are not.

> **Note:** The `monsters/5E/` duplicate subdirectory has been removed. All monster stat blocks live as flat files in `monsters/`.
