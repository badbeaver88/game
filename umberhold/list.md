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
- [ ] **Approve** a single magic model: **per-level spell cast pools** that behave like slot tiers.
- [ ] **Approve** cantrips as **unlimited use**.
- [ ] **Approve** that all non-cantrip spells consume a cast from their spell level pool.
- [ ] **Approve** recovery of spell casts only on **Long Rest at an Inn** unless a special effect says otherwise.
- [ ] **Approve** removal of the contradictory “no spell slots, only spells” wording from the README.

## 1.3 Death and Resurrection Canon
- [ ] **Approve**: **0 HP = immediate death**.
- [ ] **Approve** removing death saves from the design.
- [ ] **Approve** resurrection failure formula as:
  - `Failure Rate = 20% - Constitution Score`, minimum **1%**
- [ ] **Approve** resurrection cost as:
  - `500 gp x character level`
- [ ] **Approve** failed resurrection as a real loss unless the player chooses to reload their last inn save.

## 1.4 Save / Consequence Canon
- [ ] **Approve**: manual saves are only available at **Inns**.
- [ ] **Approve**: no autosaves in dungeons.
- [ ] **Approve**: a total party wipe sends the player to the **Graveyard Screen**.
- [ ] **Approve**: loading a saved game returns to the **last Inn save**.
- [ ] **Approve** that this is a **high-tension reload model**, not hardcore ironman.

## 1.5 Lockpicking and Trap Canon
- [ ] **Approve**: **Shadowman** is the primary lock/trap specialist.
- [ ] **Approve**: non-Shadowman characters cannot normally pick locks or disarm traps by skill.
- [ ] **Approve**: locks/traps may still be bypassed by specific spells or items.
- [ ] **Approve**: each character gets only **one attempt per lock** unless a special effect overrides it.
- [ ] **Approve**: failed lock attempts jam the lock for that specific character only.

## 1.6 Warden Identity Canon
- [ ] **Approve** the Warden’s casting stat as **PIE**.
- [ ] **Approve** removing INT-based Warden references from the README.

## 1.7 Combat Presentation Canon
- [ ] **Approve** the **4-rank tactical axis** as the only combat battlefield model.
- [ ] **Approve** deleting or ignoring the stray **20x20 combat grid** reference.

---

# 2. Exploration System Changes

## 2.1 Grid and Movement
- [ ] **Approve** the world model as strict **26x26 coordinate grids** for all regions.
- [ ] **Approve** first-person, step-based movement with **90-degree turns**.
- [ ] **Approve** movement inputs as:
  - forward
  - backward
  - turn left
  - turn right
- [ ] **Approve** no free-look and no freeform analog movement.

## 2.2 Encounter Trigger Rules
- [ ] **Approve** random encounter checks only on **successful movement into a new tile**.
- [ ] **Approve** no random encounter rolls when only turning in place.
- [ ] **Approve** encounter rates to be **region-specific and tile-tag aware**.
- [ ] **Approve** set-piece coordinates suppressing random encounters while their event is active.

## 2.3 Map Authoring Standard
- [ ] **Approve** all maps being authored from external data files, not hardcoded scene logic.
- [ ] **Approve** each tile storing at minimum:
  - coordinate
  - wall/passability
  - texture/theme
  - trigger reference
  - interactable reference
  - encounter table reference
- [ ] **Approve** adding support for one-time, repeatable, and conditional step triggers.

## 2.4 Navigation UX
- [ ] **Approve** an automap/minimap in the vertical slice.
- [ ] **Approve** visible facing direction and current coordinate in the HUD.
- [ ] **Approve** basic accessibility options for turn speed and camera comfort.

---

# 3. Combat System Changes

## 3.1 Party Formation Rules
- [ ] **Approve** the player party as a **fixed 3 front / 3 rear formation**.
- [ ] **Approve** no player-side slot sizing in version 1 of the combat system.
- [ ] **Approve** Large player races affecting stats and equipment rules, but **not consuming extra party formation slots** in v1.
- [ ] **Approve** dead party members being moved to the rear visually but not automatically replaced mid-turn.
- [ ] **Approve** party rank reordering only outside combat for the first implementation.

## 3.2 Enemy Formation Rules
- [ ] **Approve** enemy formation as:
  - Enemy Front Rank: 6 slots
  - Enemy Rear Rank: 6 slots
- [ ] **Approve** enemy size costs:
  - Medium = 1 slot
  - Large = 2 slots
  - Huge = 3 slots
  - Gigantic = 4 slots
- [ ] **Approve** large enemies occupying contiguous slots.

## 3.3 Range and Targeting
- [ ] **Approve** range validation by rank distance:
  - adjacent ranks = distance 1
  - one-rank gap = distance 2
  - two-rank gap = distance 3
- [ ] **Approve** target selection against specific enemy slot groups/portraits.
- [ ] **Approve** area effects using horizontal slot geometry where relevant.
- [ ] **Approve** invalid range feedback appearing before action resolution.

## 3.4 Action Economy
- [ ] **Approve** one primary action per combat turn in the first implementation.
- [ ] **Approve** available actions as:
  - Attack
  - Cast Spell
  - Use Item
  - Dodge/Defend
  - Equip/Swap Weapon
- [ ] **Approve** weapon swap consuming the turn in the first implementation.
- [ ] **Approve** bonus actions and reactions being deferred unless a class absolutely requires them.

## 3.5 Core Combat Math
- [ ] **Approve** using a 5E-style attack roll foundation for physical attacks.
- [ ] **Approve** using spell save DC:
  - `8 + proficiency + casting modifier`
- [ ] **Approve** status durations to tick down on clearly defined turn boundaries.
- [ ] **Approve** crit rules to be explicitly specified for all classes in `canon.md`.

## 3.6 Enemy AI
- [ ] **Approve** enemy AI profiles as explicit data-driven behavior sets.
- [ ] **Approve** melee enemies with `advance` behavior moving from rear to front when space allows.
- [ ] **Approve** ranged/caster enemies preferring rear rank unless forced forward.
- [ ] **Approve** boss AI using bespoke scripted behavior layers on top of base profiles.

## 3.7 Status System
- [ ] **Approve** a canonical condition list for the vertical slice, including at minimum:
  - Poisoned
  - Charmed
  - Blinded
  - Frightened
  - Sleep
  - Bleeding
- [ ] **Approve** defining resistance, immunity, cleansing, stacking, and timing rules in `canon.md`.

---

# 4. Character System Changes

## 4.1 Vertical Slice Class Scope
- [ ] **Approve** limiting the first playable slice to these classes:
  - Man-at-Arms
  - Shadowman
  - Friar
- [ ] **Approve** deferring the rest until the core loop is proven.

## 4.2 Vertical Slice Race Scope
- [ ] **Approve** limiting the first playable slice to these races:
  - Human
  - Stoutling
  - Hillkin
- [ ] **Approve** deferring the rest until later production.

## 4.3 Character Creation Scope
- [ ] **Approve** first implementation character creation flow as:
  - sex
  - race
  - class
  - vocation
  - roll stats
  - starting gold
  - keep/discard
  - name
- [ ] **Approve** no class/race restrictions in the first playable slice unless balance requires it.

## 4.4 Vocation Scope
- [ ] **Approve** vocations as **passive background perks only** in the first implementation.
- [ ] **Approve** no vocation-specific dialogue or quest branching in the vertical slice.

## 4.5 Luck Integration
- [ ] **Approve** Luck affecting at least these systems in the final rules pass:
  - trap avoidance or trap saves
  - rare loot / event rolls
  - initiative tie-breaks or crit-related subrules
- [ ] **Approve** removing Luck later if it cannot be given enough meaningful uses.

---

# 5. Progression, Economy, and Inventory Changes

## 5.1 XP Curve
- [ ] **Approve** using a **5x 5E XP curve** as the long-term progression model.
- [ ] **Approve** producing an explicit level table for levels **1-10** in `canon.md`.
- [ ] **Approve** using a reduced temporary cap of **3 to 5** in the vertical slice.

## 5.2 Inventory Rules
- [ ] **Approve** inventory as both **weight-limited** and **slot-limited** where needed by UI.
- [ ] **Approve** no item stacking.
- [ ] **Approve** equipped items counting toward carry burden.
- [ ] **Approve** trading items between party members.

## 5.3 Encumbrance Formula
- [ ] **Approve** defining a hard carry-cap formula tied primarily to **STR**.
- [ ] **Approve** preventing item pickup when over capacity rather than allowing overloaded movement penalties.

## 5.4 Shop and Economy Rules
- [ ] **Approve** creating explicit pricing tables for:
  - resting
  - healing
  - resurrection
  - identification
  - potions
  - weapon/armor resale
- [ ] **Approve** shops as mostly static inventories in the vertical slice.
- [ ] **Approve** a fixed resale percentage for clarity.

## 5.5 Ammunition Decision
- [ ] **Approve** one of the following for the first slice:
  - **Option A:** abstract ammo and do not track arrows/bolts yet
  - **Option B:** fully track ammo as non-stacking items
- [ ] **Approve** default recommendation: **Option A** for vertical slice simplicity.

---

# 6. Narrative and Quest Changes

## 6.1 Narrative Scope Lock
- [ ] **Approve** the first vertical slice story as:
  - life in Umberhold
  - disappearances begin
  - Gravenhollow Manor opens
  - villagers are missing
  - the manor reveals necromantic corruption
  - first major boss is defeated
- [ ] **Approve** not building all nine regions before the opening act is polished.

## 6.2 Narrative Flag System
- [ ] **Approve** a global story flag dictionary driving:
  - quest states
  - NPC dialogue changes
  - event conditions
  - set-piece outcomes
  - boss defeat persistence
- [ ] **Approve** all fixed encounters and story events checking flags before firing.

## 6.3 Set-Piece Authoring
- [ ] **Approve** set pieces as data-driven scripted events, not hardcoded one-offs.
- [ ] **Approve** support for:
  - dialogue
  - battle start
  - item grant
  - flag changes
  - NPC spawn/despawn
  - conditional branch by prior choices

## 6.4 NPC Reactivity Scope
- [ ] **Approve** “intelligent NPCs” being implemented as **conditional authored dialogue**, not generative AI behavior.
- [ ] **Approve** deferring advanced NPC simulation.

---

# 7. UI/UX Changes

## 7.1 Combat UI Priorities
- [ ] **Approve** combat HUD must clearly show:
  - party front/rear
  - enemy front/rear
  - enemy slot occupancy
  - targetable vs untargetable enemies
  - initiative order
  - status icons
  - combat log
- [ ] **Approve** range failure messaging such as:
  - “Target out of range”
  - “No valid target in selected rank”

## 7.2 Explore UI Priorities
- [ ] **Approve** exploration HUD must show:
  - minimap / automap
  - facing direction
  - current coordinate
  - party status
  - active buffs
  - interact prompt when relevant

## 7.3 Input Philosophy
- [ ] **Approve** keyboard-first controls with mouse-assisted targeting.
- [ ] **Approve** right-click or Escape to cancel pending target selection.
- [ ] **Approve** keyboard-only fallback support where practical.

## 7.4 Accessibility
- [ ] **Approve** minimum accessibility support in the vertical slice:
  - key rebinding
  - turn speed/snap turn settings
  - subtitle/combat log readability
  - color-safe status indicators

---

# 8. Technical and Pipeline Changes

## 8.1 Engine Decision
- [ ] **Approve** selecting the engine before deeper implementation begins.
- [ ] **Approve** making engine choice based on:
  - first-person grid rendering ease
  - UI tooling
  - data loading workflow
  - save/load reliability
  - team familiarity

## 8.2 Data-Driven Architecture
- [ ] **Approve** external data files for:
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
- [ ] **Approve** schema validation for content files.

## 8.3 Tooling Requirement
- [ ] **Approve** building or adopting tools for:
  - map editing
  - encounter table editing
  - dialogue editing
  - content validation
  - save inspection/debugging
- [ ] **Approve** this as a production requirement, not a nice-to-have.

## 8.4 Save System Scope
- [ ] **Approve** multiple manual save slots at Inns.
- [ ] **Approve** saving party roster, items, gold, flags, fixed encounter states, and world progression.
- [ ] **Approve** random encounters not needing per-encounter persistence.

## 8.5 Testing Strategy
- [ ] **Approve** adding automated validation for:
  - range checks
  - enemy advance logic
  - slot occupancy
  - save/load integrity
  - resurrection math
  - flag gating
- [ ] **Approve** simulation tests for combat edge cases.

---

# 9. Vertical Slice Scope Changes

## 9.1 Slice Boundary
- [ ] **Approve** the vertical slice as:
  - Umberhold village hub
  - Gravenhollow Manor first dungeon experience
  - 1 boss
  - 2-3 side quests
  - full inn/shop/chantry loop
- [ ] **Approve** no expansion beyond this until the slice is fun and stable.

## 9.2 Content Count Targets
- [ ] **Approve** approximate vertical slice targets:
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
- [ ] **Approve** vertical slice success criteria:
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
- [ ] **Approve** creation of these follow-up docs:
  - `canon.md` — final rules and formulas
  - `slice.md` — exact first playable scope
  - `schemas.md` — content data formats
  - `combat.md` — combat rules and diagrams
  - `economy.md` — XP, gold, prices, carry formulas

## 10.2 README Cleanup Pass
- [ ] **Approve** a future README cleanup to remove contradictions after canon decisions are signed off.

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

- [ ] Use **STR / AGI / CON / INT / PIE / PRE / LCK**
- [ ] Use **per-level spell cast pools** with free cantrips
- [ ] Use **0 HP = death**
- [ ] Use resurrection failure = **20% - CON**, min 1%
- [ ] Use **Inn-only manual saves**
- [ ] Make **Shadowman** the lock/trap specialist
- [ ] Make **Warden PIE-based**
- [ ] Use **4-rank combat only**
- [ ] Use **3 front / 3 rear party formation**
- [ ] Use **6-slot enemy ranks**
- [ ] Build **Umberhold + Gravenhollow** first
- [ ] Limit the vertical slice to **3 classes / 3 races / 1 dungeon / 1 boss**
- [ ] Make the whole project **data-driven** from the start

---

# 13. Approval Note

Once this list is approved, the next best step is to generate:
1. `canon.md` from the approved decisions
2. `slice.md` from the approved vertical slice scope
3. `schemas.md` for implementation-ready data formats
