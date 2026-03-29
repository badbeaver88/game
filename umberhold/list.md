# Umberhold Approval Change List

This document converts `gap.md` into a **clear set of changes to approve**.

Use this as a decision checklist. If approved, these items should become the basis for `canon.md` and the first vertical slice.

---

## How to Use This List

For each item, approve one of:
- **Approve as written**
- **Approve with edits**
- **Reject / revisit later**

Suggested marker:
- `[ ]` pending
- `[x]` approved
- `[-]` approved with edits

---

# 1. Canon Rules Changes

## 1.1 Stat Naming Standardization
- [x] **Approve** one canonical stat set for all systems and UI:
  - **STR** = Strength
  - **AGI** = Agility
  - **CON** = Constitution
  - **INT** = Intellect
  - **PIE** = Piety
  - **PRE** = Personality
  - **LCK** = Luck
- [x] **Approve** replacing all mixed 5E labels in content with these terms.

## 1.2 Magic System Canon
- [x] **Approve** a single magic model: **per-level spell cast pools** that behave like slot tiers.
- [x] **Approve** cantrips as **unlimited use**.
- [x] **Approve** that all non-cantrip spells consume a cast from their spell level pool.
- [-] **Approve** recovery of spell casts only on **Long Rest at an Inn** unless a special effect says otherwise. (Long and short rests have been removed from the game. Now Resting at an inn takes 8 hours and functions like a long rest; all resources are recovered, including spell slots, hit points and class resources.) 
- [x] **Approve** removal of the contradictory “no spell slots, only spells” wording from the README.

## 1.3 Death and Resurrection Canon
- [x] **Approve**: **0 HP = immediate death**.
- [x] **Approve** removing death saves from the design.
- [x] **Approve** resurrection failure formula as:
  - `Failure Rate = 20% - Constitution Score`, minimum **1%**
- [x] **Approve** resurrection cost as:
  - `500 gp x character level`
- [x] **Approve** failed resurrection as a real loss unless the player chooses to reload their last inn save. (This mechanic can be bypassed by players saving their game before attempting a resurrection. To prevent this, failure to resurrect causes the character to be turned to ash and even if a previous saved game is loaded, the player is gone, permanently).

## 1.4 Save / Consequence Canon
- [x] **Approve**: manual saves are only available at **Inns**.
- [x] **Approve**: no autosaves in dungeons. (Some areas in dungeons allow the party to rest, functioning like an inn. These areas are clearly identified and typically require the party to clear a set number of encounters to make them safe.)
- [x] **Approve**: a total party wipe sends the player to the **Graveyard Screen**.
- [x] **Approve**: loading a saved game returns to the **last Inn save**.
- [x] **Approve** that this is a **high-tension reload model**, not hardcore ironman.

## 1.5 Lockpicking and Trap Canon
- [x] **Approve**: **Shadowman** is the primary lock/trap specialist. (The Shadowman class is the only one who can pick locks and find and remove traps).
- [x] **Approve**: non-Shadowman characters cannot normally pick locks or disarm traps by skill.
- [x] **Approve**: locks/traps may still be bypassed by specific spells or items.
- [x] **Approve**: each character gets only **one attempt per lock** unless a special effect overrides it.
- [x] **Approve**: failed lock attempts jam the lock for that specific character only.

## 1.6 Warden Identity Canon
- [x] **Approve** the Warden’s casting stat as **PIE**.
- [x] **Approve** removing INT-based Warden references from the README.

## 1.7 Combat Presentation Canon
- [x] **Approve** the **4-rank tactical axis** as the only combat battlefield model.
- [x] **Approve** deleting or ignoring the stray **20x20 combat grid** reference.

---

# 2. Exploration System Changes

## 2.1 Grid and Movement
- [x] **Approve** the world model as strict **26x26 coordinate grids** for all regions.
- [x] **Approve** first-person, step-based movement with **90-degree turns**.
- [x] **Approve** movement inputs as:
  - forward
  - backward
  - turn left
  - turn right
- [x] **Approve** no free-look and no freeform analog movement.

## 2.2 Encounter Trigger Rules
- [x] **Approve** random encounter checks only on **successful movement into a new tile**.
- [x] **Approve** no random encounter rolls when only turning in place.
- [x] **Approve** encounter rates to be **region-specific and tile-tag aware**.
- [x] **Approve** set-piece coordinates suppressing random encounters while their event is active.

## 2.3 Map Authoring Standard
- [x] **Approve** all maps being authored from external data files, not hardcoded scene logic.
- [x] **Approve** each tile storing at minimum:
  - coordinate
  - wall/passability
  - texture/theme
  - trigger reference
  - interactable reference
  - encounter table reference
- [x] **Approve** adding support for one-time, repeatable, and conditional step triggers.

## 2.4 Navigation UX
- [x] **Approve** an automap/minimap in the vertical slice.
- [x] **Approve** visible facing direction and current coordinate in the HUD.
- [x] **Approve** basic accessibility options for turn speed and camera comfort.

## 2.5 Time System
- [x] **Approve** a **discrete 6-second world time step** as the core unit for timed systems.
- [x] **Approve** one **successful movement into a new tile** consuming **6 seconds**.
- [x] **Approve** one **full combat round** (all combatants act) consuming **6 seconds**.
- [x] **Approve** **no passive time**; the world remains static until the player acts.
- [x] **Approve** time of day being shown only as an **8-phase day cycle** below the minimap, not as an exact clock.
- [x] **Approve** the day phases as:
  - Dead of Night
  - Black Hours
  - First Light
  - High Morning
  - Sun at Zenith
  - Fading Light
  - Gloaming
  - Nightfall
- [x] **Approve** most shops operating during **First Light** through **Fading Light**.
- [x] **Approve** **inns/taverns** remaining open at all hours.
- [x] **Approve** spell durations, status effects, and world interactions all using this same underlying time model.

---

# 3. Combat System Changes

## 3.1 Party Formation Rules
- [x] **Approve** the player party as a **fixed 3 front / 3 rear formation**.
- [x] **Approve** no player-side slot sizing in version 1 of the combat system.
- [x] **Approve** Large player races affecting stats and equipment rules, but **not consuming extra party formation slots** in v1.
- [-] **Approve** dead party members being moved to the rear visually but not automatically replaced mid-turn. (The party oredr is 1-6, assuming a full party of 6. The first 3 are in the front rank, and the last 3 are in the rear rank. Dead characters are moved to back of the party, and the living characters move up a slot.) 
- [x] **Approve** party rank reordering only outside combat for the first implementation. (By drag and dropping on another character's portrait to switch positions)

## 3.2 Enemy Formation Rules
- [x] **Approve** enemy formation as:
  - Enemy Front Rank: 6 slots
  - Enemy Rear Rank: 6 slots
- [x] **Approve** enemy size costs:
  - Medium = 1 slot
  - Large = 2 slots
  - Huge = 3 slots
  - Gigantic = 4 slots
- [-] **Approve** large enemies occupying contiguous slots. (I'm unsure what this means)

## 3.3 Range and Targeting
- [x] **Approve** range validation by rank distance:
  - adjacent ranks = distance 1
  - one-rank gap = distance 2
  - two-rank gap = distance 3
- [x] **Approve** target selection against specific enemy slot groups/portraits.
- [x] **Approve** area effects using horizontal slot geometry where relevant.
- [x] **Approve** invalid range feedback appearing before action resolution.

## 3.4 Action Economy
- [x] **Approve** one primary action per combat turn in the first implementation.
- [x] **Approve** available actions as:
  - Attack
  - Cast Spell
  - Use Item
  - Dodge/Defend
  - Equip/Swap Weapon
- [x] **Approve** weapon swap consuming the turn in the first implementation.
- [-] **Approve** bonus actions and reactions being deferred unless a class absolutely requires them. (Reactions ahve been removed from the game)

## 3.5 Core Combat Math
- [x] **Approve** using a 5E-style attack roll foundation for physical attacks.
- [x] **Approve** using spell save DC:
  - `8 + proficiency + casting modifier`
- [x] **Approve** status durations to tick down on clearly defined turn boundaries.
- [x] **Approve** crit rules to be explicitly specified for all classes in `canon.md`.

## 3.6 Enemy AI
- [x] **Approve** enemy AI profiles as explicit data-driven behavior sets.
- [x] **Approve** melee enemies with `advance` behavior moving from rear to front when space allows.
- [x] **Approve** ranged/caster enemies preferring rear rank unless forced forward.
- [x] **Approve** boss AI using bespoke scripted behavior layers on top of base profiles.

## 3.7 Status System (I've provided a list of conditions)
- [-] **Approve** a canonical condition list for the vertical slice, including at minimum:
  - Poisoned
  - Charmed
  - Blinded
  - Frightened
  - Sleep
  - Bleeding
- [x] **Approve** defining resistance, immunity, cleansing, stacking, and timing rules in `canon.md`.

---

# 4. Character System Changes

## 4.1 Vertical Slice Class Scope
- [ ] **Approve** limiting the first playable slice to these classes: (I'd like all classes in)
  - Man-at-Arms
  - Shadowman
  - Friar
- [ ] **Approve** deferring the rest until the core loop is proven.

## 4.2 Vertical Slice Race Scope
- [ ] **Approve** limiting the first playable slice to these races: (I'd like all races in)
  - Human
  - Stoutling
  - Hillkin
- [ ] **Approve** deferring the rest until later production.

## 4.3 Character Creation Scope
- [x] **Approve** first implementation character creation flow as:
  - sex
  - race
  - class
  - vocation
  - roll stats
  - starting gold
  - keep/discard
  - name
- [x] **Approve** no class/race restrictions in the first playable slice unless balance requires it.

## 4.4 Vocation Scope
- [x] **Approve** vocations as **passive background perks only** in the first implementation.
- [x] **Approve** no vocation-specific dialogue or quest branching in the vertical slice.

## 4.5 Luck Integration
- [-] **Approve** Luck affecting at least these systems in the final rules pass: (I will provide Luck rules soon)
  - trap avoidance or trap saves
  - rare loot / event rolls
  - initiative tie-breaks or crit-related subrules
- [ ] **Approve** removing Luck later if it cannot be given enough meaningful uses.

---

# 5. Progression, Economy, and Inventory Changes

## 5.1 XP Curve
- [x] **Approve** using a **5x 5E XP curve** as the long-term progression model.
- [x] **Approve** producing an explicit level table for levels **1-10** in `canon.md`.
- [ ] **Approve** using a reduced temporary cap of **3 to 5** in the vertical slice.

## 5.2 Inventory Rules
- [x] **Approve** inventory as both **weight-limited** and **slot-limited** where needed by UI. 
- [x] **Approve** no item stacking.
- [x] **Approve** equipped items counting toward carry burden.
- [x] **Approve** trading items between party members.

The paperdoll has the following slots: Torso (armor), main and offhand (offhand shaded out if a two handed weapon is equiped in main hand), Feet (boots), Head (cap, helm, hat), Hands (gloves, bracers), Neck (necklace), Fingers (two rings are allowed), Special (4 slots are available for various items like Ioun Stones, broaches and the like). 



## 5.3 Encumbrance Formula
- [x] **Approve** defining a hard carry-cap formula tied primarily to **STR**.
- [x] **Approve** preventing item pickup when over capacity rather than allowing overloaded movement penalties.

## 5.4 Shop and Economy Rules
- [x] **Approve** creating explicit pricing tables for:
  - resting
  - healing
  - resurrection
  - identification
  - potions
  - weapon/armor resale
- [x] **Approve** shops as mostly static inventories in the vertical slice.
- [x] **Approve** a fixed resale percentage for clarity.

## 5.5 Ammunition Decision
- [x] **Approve** one of the following for the first slice: (It is assumed characters have unlimited ammunition for the ranged weapons they carry; this is not recorded or tracked and is a QOL mechanic).
  - **Option A:** abstract ammo and do not track arrows/bolts yet
  - **Option B:** fully track ammo as non-stacking items
- [ ] **Approve** default recommendation: **Option A** for vertical slice simplicity.

---

# 6. Narrative and Quest Changes

## 6.1 Narrative Scope Lock
- [x] **Approve** the first vertical slice story as:
  - life in Umberhold
  - disappearances begin
  - Gravenhollow Manor opens
  - villagers are missing
  - the manor reveals necromantic corruption
  - first major boss is defeated
- [x] **Approve** not building all nine regions before the opening act is polished.

## 6.2 Narrative Flag System
- [x] **Approve** a global story flag dictionary driving:
  - quest states
  - NPC dialogue changes
  - event conditions
  - set-piece outcomes
  - boss defeat persistence
- [x] **Approve** all fixed encounters and story events checking flags before firing. (Most fixed encounters will be larger combats with a fixed number of monsters, and often a unique, named 'boss' monster not encountered anywhere else.)

## 6.3 Set-Piece Authoring
- [-] **Approve** set pieces as data-driven scripted events, not hardcoded one-offs. (There may be some dialogue before combat begins, and occasionally combat may be avoided by good parley).
- [x] **Approve** support for:
  - dialogue
  - battle start
  - item grant
  - flag changes
  - NPC spawn/despawn
  - conditional branch by prior choices


QUEST ITEMS - quest items are necessary for completion of the game. When the party recieve these, they go into a separate Quest Items tab on the UI. These items cannot be dropped, sold or lost; they are permanent inventory once picked up in order to ensure the game can be completed.


## 6.4 NPC Reactivity Scope
- [x] **Approve** “intelligent NPCs” being implemented as **conditional authored dialogue**, not generative AI behavior.
- [x] **Approve** deferring advanced NPC simulation.

---

# 7. UI/UX Changes

## 7.1 Combat UI Priorities
- [x] **Approve** combat HUD must clearly show:
  - party front/rear
  - enemy front/rear
  - enemy slot occupancy
  - targetable vs untargetable enemies
  - initiative order
  - status icons
  - combat log
- [x] **Approve** range failure messaging such as:
  - “Target out of range”
  - “No valid target in selected rank”

## 7.2 Explore UI Priorities
- [x] **Approve** exploration HUD must show:
  - minimap / automap
  - facing direction
  - current coordinate
  - party status
  - active buffs
  - interact prompt when relevant

## 7.3 Input Philosophy
- [x] **Approve** keyboard-first controls with mouse-assisted targeting.
- [x] **Approve** right-click or Escape to cancel pending target selection.
- [x] **Approve** keyboard-only fallback support where practical.

## 7.4 Accessibility
- [x] **Approve** minimum accessibility support in the vertical slice:
  - key rebinding
  - turn speed/snap turn settings
  - subtitle/combat log readability
  - color-safe status indicators

---

# 8. Technical and Pipeline Changes

## 8.1 Engine Decision
- [x] **Approve** selecting the engine before deeper implementation begins.
- [x] **Approve** making engine choice based on:
  - first-person grid rendering ease
  - UI tooling
  - data loading workflow
  - save/load reliability
  - team familiarity

## 8.2 Data-Driven Architecture
- [x] **Approve** external data files for:
  - maps
  - tiles
  - encounters
  - monsters
  - items
  - spells
  - races
  - classes
  - vocations
  - quests
  - dialogue
  - shops
  - flags
- [x] **Approve** schema validation for content files.

## 8.3 Tooling Requirement
- [x] **Approve** building or adopting tools for:
  - map editing
  - encounter table editing
  - dialogue editing
  - content validation
  - save inspection/debugging
- [x] **Approve** this as a production requirement, not a nice-to-have.

## 8.4 Save System Scope
- [x] **Approve** multiple manual save slots at Inns. (5 saves are available; A-E. These can be overwritten.)
- [x] **Approve** saving party roster, items, gold, flags, fixed encounter states, and world progression.
- [x] **Approve** random encounters not needing per-encounter persistence.

## 8.5 Testing Strategy
- [x] **Approve** adding automated validation for:
  - range checks
  - enemy advance logic
  - slot occupancy
  - save/load integrity
  - resurrection math
  - flag gating
- [x] **Approve** simulation tests for combat edge cases.

---

# 9. Vertical Slice Scope Changes

## 9.1 Slice Boundary
- [x] **Approve** the vertical slice as:
  - Umberhold village hub
  - Gravenhollow Manor first dungeon experience
  - 1 boss
  - 2-3 side quests
  - full inn/shop/chantry loop
- [x] **Approve** no expansion beyond this until the slice is fun and stable.

## 9.2 Content Count Targets
- [-] **Approve** approximate vertical slice targets: (I'd like all classes and races in)
  - 1 town hub
  - 1 dungeon map
  - 8-12 monsters
  - 20-30 items
  - 10-15 spells/abilities
  - 3 playable classes
  - 3 playable races
  - 1 mini-boss
  - 1 boss

## 9.3 Done Criteria
- [x] **Approve** vertical slice success criteria:
  - create a party
  - explore a 3D 26x26 map
  - trigger random and fixed encounters
  - fight using 4-rank / 6-slot combat
  - loot and equip gear
  - return to town
  - heal, resurrect, rest, and save
  - complete first major story objective

---

# 10. Documentation Changes

## 10.1 New Required Docs
- [x] **Approve** creation of these follow-up docs:
  - `canon.md` — final rules and formulas
  - `slice.md` — exact first playable scope
  - `schemas.md` — content data formats
  - `combat.md` — combat rules and diagrams
  - `economy.md` — XP, gold, prices, carry formulas

## 10.2 README Cleanup Pass
- [x] **Approve** a future README cleanup to remove contradictions after canon decisions are signed off.

---

# 11. Priority Approval Order

If you want to approve in the best sequence, do it in this order:

## Priority 1 — Must decide first
- [ ] stat naming standard
- [ ] magic model
- [ ] death/resurrection model
- [ ] save model
- [ ] party formation rules
- [ ] Warden casting stat
- [ ] combat battlefield model

## Priority 2 — Needed for prototyping
- [ ] encounter trigger rules
- [ ] action economy
- [ ] core combat math direction
- [ ] enemy AI model
- [ ] vertical slice class/race scope
- [ ] inventory / encumbrance rules

## Priority 3 — Needed for production scaling
- [ ] data architecture
- [ ] tooling plan
- [ ] narrative flag system
- [ ] quest/set-piece authoring format
- [ ] accessibility baseline
- [ ] testing strategy

## Priority 4 — Needed before content expansion
- [ ] full class tables
- [ ] full spell libraries
- [ ] economy balancing tables
- [ ] all-region world plan

---

# 12. Recommended Defaults Summary

If you want the shortest path to approval, these are the recommended defaults:

- [x] Use **STR / AGI / CON / INT / PIE / PRE / LCK**
- [x] Use **per-level spell cast pools** with free cantrips
- [x] Use **0 HP = death**
- [x] Use resurrection failure = **20% - CON**, min 1%
- [x] Use **Inn-only manual saves**
- [x] Make **Shadowman** the lock/trap specialist
- [x] Make **Warden PIE-based**
- [x] Use **4-rank combat only**
- [x] Use **3 front / 3 rear party formation**
- [x] Use **6-slot enemy ranks**
- [x] Build **Umberhold + Gravenhollow** first
- [-] Limit the vertical slice to **3 classes / 3 races / 1 dungeon / 1 boss**
- [x] Make the whole project **data-driven** from the start

---

# 13. Approval Note

Once this list is approved, the next best step is to generate:
1. `canon.md` from the approved decisions
2. `slice.md` from the approved vertical slice scope
3. `schemas.md` for implementation-ready data formats
