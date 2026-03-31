# Magical Items Meta

Extracted from the master design document (see `DESIGN.md`).

## Summary
`DESIGN.md` clearly states that magical items are important to progression, but it does **not** currently define any actual named magical items.

So this category is effectively:
- **conceptually important**
- **content-wise empty**

---

## What `DESIGN.md` Says About Magical Items

Magical items are described as:
- uncommon/rare rewards found in dangerous grids
- a major source of progression and power spikes
- permanent items with no durability loss
- sometimes sold in minor form by **Etheldreda** at the Alchemist’s Mortar
- sometimes hidden at fixed coordinates or guarded by bosses
- sometimes requiring **Identify** or shop identification

---

## What Is Already Present Indirectly

Related support content already exists for magical-item systems:
- item identification is supported by **Identify** and shop service
- rare magic item rewards are part of the reward loop
- Tinkerfolk has a race perk tied to damaging magic items
- shops and loot systems are built with room for magical items

---

## What Is Missing

### No named magical items yet
There are currently no specific entries for:
- weapons
- armor
- rings
- amulets
- relics
- staves/wands/rods
- potions with named magical effects
- cursed items
- quest relics

### No magical-item schema yet
You still need consistent fields like:
- item name
- type / slot
- rarity
- weight
- value
- passive effect
- active effect if any
- charges if any
- identification text
- lore text
- acquisition source

---

## High-Priority Magical Item Buckets To Author

### 1. Early Foundational Magic Gear
Needed for first dungeon progression:
- +accuracy weapons
- +damage weapons
- +AC armor/shields
- simple stat-boost charms
- anti-undead tools

### 2. Utility Magic Items
Needed for exploration and tension:
- trap/lock support items
- healing or curative items
- light-producing relics
- emergency escape or ward items

### 3. Class-Support Magic Items
Needed to reinforce identity:
- Shadowman poison/stealth tools
- Friar holy symbols/relics
- Hedge Wizard implements
- Troubadour instruments
- Warden marksman gear
- Crusader sanctified weapons
- Man-at-Arms defensive gear

### 4. Unique Boss / Set-Piece Rewards
Needed for memorable progression:
- one-of-a-kind manor relics
- church relic fragments
- necromantic artifacts
- anti-lich or anti-undead legendary pieces

---

## Magical Item Gaps Checklist

- [ ] Define a magical-item schema
- [ ] Create early-game uncommon magical item list
- [ ] Create boss-drop magical item list
- [ ] Create Alchemist magical consumables list
- [ ] Create identified vs unidentified item rules text
- [ ] Decide whether cursed items exist in Umberhold
- [ ] Decide whether magical items can have charges
- [ ] Define how Tinkerfolk interacts with damaging magic items
- [ ] Add lore blurbs to key relics

---

## Suggested Minimum Vertical Slice Content

For the Umberhold + Manor slice, consider authoring at least:
- 3-5 magical weapons
- 2-3 magical armor/shield pieces
- 3-5 magical consumables
- 2-3 utility relics
- 1 mini-boss reward
- 1 major boss reward

---

## Status
This is one of your **largest pure content gaps**.
The system around magical items exists in outline, but the actual item library still needs to be authored almost from scratch.

> **Note:** The Lesser magical item tier has been authored and lives in `items/lesser-magical-items.md`.
