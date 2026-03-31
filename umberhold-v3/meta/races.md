# Races Meta

Extracted from the master design document (see `DESIGN.md`).

## Summary
`DESIGN.md` defines **6 races** with:
- size
- basic stat bonuses
- one major perk/resistance package

This is a solid base. The race list is mostly present, but it still needs **canon cleanup and deeper implementation fields**.

---

## Races Found

| Race | Size | Current Mechanical Definition |
|---|---|---|
| Human | Medium | +1 to four random stats (max 18); Versatility |
| Everkin | Medium | +1 AGI, +1 INT; bow accuracy, bow crit boost, sleep/charm resistance |
| Deepfolk | Medium | +1 CON, +1 STR; +1 HP/level, poison save bonus |
| Stoutlings | Small | +1 LCK, +1 AGI; +4 lockpicking, +2 all saves |
| Tinkerfolk | Small | +1 INT, +1 LCK; magic item crit effect doubling on natural 20 |
| Hillkin | Large | +1 CON, +1 STR; Base AC 11; -4 AGI saves |

---

## What Is Already Defined

Every race currently has at least:
- name
- size
- stat bonuses
- one perk/resistance identity

Hillkin is the most mechanically distinctive because it also defines:
- custom base AC
- explicit save penalty
- large body identity

---

## What Still Needs To Be Authored

### For all races
- final canonical stat labels in Umberhold-native wording
- lore paragraph / culture snapshot
- visual identity notes
- naming guidance if desired
- exact save labels in final terminology
- interaction with encumbrance if any
- interaction with equipment fitting if any
- interaction with party formation if any
- whether NPCs react differently by race

### Human
Needs clarification on:
- how the four random bonuses are rolled/generated
- whether the random result can hit already high stats
- whether Human gets any secondary perk beyond versatility flavor

### Everkin
Needs clarification on:
- whether bow crit expansion applies to all ranged bows or only certain weapon families
- exact wording for sleep/charm resistance
- deeper cultural identity and role in the world

### Deepfolk
Needs clarification on:
- whether +1 HP per level applies retroactively at creation and level-up
- whether poison bonus applies to saves only, damage only, or both
- deeper cultural identity and role in the world

### Stoutlings
Needs clarification on:
- whether the lockpicking bonus matters if only Shadowman can pick locks
- whether the save bonus is truly universal
- whether Small size has any exploration/combat impact

### Tinkerfolk
Needs clarification on:
- what counts as a “damaging magic item”
- whether the doubled effect applies only to damage dice or total effect
- how common damaging magic items will actually be

### Hillkin
Needs clarification on:
- whether Large size has gameplay implications beyond base AC and save penalty
- whether Hillkin use standard armor costs/sizing
- whether Large size changes party rank occupancy or not
- whether special equipment restrictions exist

---

## Race Gaps Checklist

- [ ] Rewrite race rules without explicit 5E references in public-facing docs
- [ ] Standardize stat naming across all race entries
- [ ] Define size gameplay effects for Small / Medium / Large
- [ ] Define whether race affects equipment fit/cost
- [ ] Define whether race affects social/NPC reactions
- [ ] Add short lore blurbs for all 6 races
- [ ] Add visual descriptors for portraits/sprites/models
- [ ] Resolve Stoutlings lockpicking synergy with Shadowman-only lock rules
- [ ] Resolve Hillkin size implications in the combat system

---

## Recommended Authoring Priority
1. Hillkin
2. Stoutlings
3. Human
4. Everkin
5. Deepfolk
6. Tinkerfolk

The top two have the most mechanical edge-case risk.

> **Note:** Individual race files now exist in `races/`.
