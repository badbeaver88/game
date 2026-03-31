# Umberhold NPCs Meta

Extracted from the master design document (see `DESIGN.md`).

> Full authored follow-up now lives in:
> - `umberhold/umberhold-village-hub.md`
> - `umberhold/umberhold-npc-dialogue.md`

## Summary
`DESIGN.md` defines **5 core service NPCs** in Umberhold.
They are excellent anchors for the town loop, but currently exist mostly as:
- name
- location
- primary service

They still need full authoring.

---

## NPCs Found in Umberhold

| NPC | Location | Service |
|---|---|---|
| Bartholomew | Umberhold Inn | Long Rest, Create/Delete/Swap characters |
| Oswaldine | Iron Shovel & Scutage | Buy/Sell gear, Identify items |
| Acolyte Gidney | Solcine Chantry | Healing, Resurrection |
| Wymarc | The Bailiff’s Desk | Narrative side-quests |
| Etheldreda | Alchemist’s Mortar | Potions and minor magical items |

---

## Additional Named Story NPCs Referenced Outside the Core Town Loop
These are present in `DESIGN.md`, but are not defined as active Umberhold service NPCs:
- Lord Patriarch
- High Priest Pancras
- Lich King

These matter for world/narrative planning, but not the immediate village hub implementation.

---

## What Is Already Defined

### Bartholomew
Defined as:
- innkeeper
- rest/save/roster management role

### Oswaldine
Defined as:
- merchant / identifier
- handles gear economy

### Acolyte Gidney
Defined as:
- healer/resurrection specialist
- has some resurrection flavor dialogue tied to Constitution quality
- has explicit resurrection pricing and failure formula context around him

### Wymarc
Defined as:
- bailiff / quest-giver
- handles culling contracts / side-quest direction

### Etheldreda
Defined as:
- alchemist
- potion and minor magical item vendor

---

## What Still Needs To Be Authored

### For every Umberhold NPC
You still need:
- appearance / visual brief
- personality summary
- default greeting
- repeat dialogue
- quest-state dialogue variations
- service UI text
- lore tie to Umberhold
- relationship to the manor crisis
- opinion of the player party / village poor

### Bartholomew needs
- inn cost if any
- save/rest dialogue
- roster management framing
- any rumors/tips dialogue
- personality and backstory

### Oswaldine needs
- shop inventory
- identify pricing
- buy/sell rates
- item flavor dialogue
- personality and shop tone

### Acolyte Gidney needs
- healing pricing/services
- resurrection interaction flow
- failure/success dialogue states
- church lore
- relationship to missing clergy / Pancras / Patriarch plot

### Wymarc needs
- starter quest list
- culling contract structure
- reward tables
- side-quest progression dialogue
- local political role in Umberhold

### Etheldreda needs
- potion list
- minor magical item list
- alchemy flavor dialogue
- ingredient or side-service hooks if any
- personality and possible occult undertones

---

## NPC Gaps Checklist

- [ ] Write short bios for all 5 NPCs
- [ ] Write first-meeting dialogue for all 5 NPCs
- [ ] Write repeat dialogue for all 5 NPCs
- [ ] Write quest-state dialogue branches
- [ ] Create shop/service inventories and prices
- [ ] Define each NPC’s relationship to the manor events
- [ ] Define whether any NPC can leave, die, change, or unlock new services
- [ ] Add rumors / lore snippets to support the opening act

---

## Suggested Minimum Dialogue Pass for Vertical Slice

For each of the 5 NPCs, create at least:
- 1 intro line
- 3 repeat ambient lines
- 2 pre-manor quest lines
- 2 post-first-boss lines
- 1 crisis/escalation line

That alone will make Umberhold feel reactive and alive.

---

## Status
This category is **well-seeded but underwritten**.
The NPC framework is strong; the actual authored dialogue and service data still need to be built.
