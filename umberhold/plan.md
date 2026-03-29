# Umberhold Implementation Plan

## Goal
Build **Umberhold** as a **first-person, grid-based 3D RPG** with:
- **26x26 regional maps**
- **step-based exploration** with 90-degree turns
- **party-of-six** character management
- **tactical 4-rank combat** with enemy slot sizing and range rules
- **high-stakes town loop** built around inn-only saving, recovery, and progression
- **data-driven content** for regions, encounters, monsters, classes, items, spells, and narrative flags

This plan turns the current `README.md` into a practical production roadmap.

---

## 1. High-Level Read of the README

The README describes a strong game identity with four defining pillars:

1. **Classic dungeon crawling**
   - 1st-person exploration
   - grid movement
   - heavy atmosphere
   - mapping and route planning matter

2. **Tactical rank combat**
   - 4-rank battlefield
   - 6-slot enemy ranks
   - range-limited actions
   - enemy advance behavior creates positional tactics without free movement

3. **High-stakes progression**
   - inn-only saves
   - expensive resurrection with failure chance
   - limited spell recovery
   - encumbrance and inventory pressure

4. **Narrative-forward dark fantasy**
   - stronger story emphasis than typical blobbers
   - set-piece encounters and narrative flags
   - village hub + regional progression + final northern campaign

The concept is compelling, but the design is also **large in scope**. The safest approach is to build it in **layers**, proving the exploration/combat loop first, then adding content and secondary systems.

---

## 2. Important Design Conflicts to Resolve Early

The README contains a few contradictions. These should be made canonical before production begins.

### 2.1 Magic system conflict
The document says both:
- spellcasters use **5E spell slots**, and
- there are **no spell slots**, only spells-per-rest counts.

**Recommendation:**
Use a **slot-like per-level cast pool** as the canonical implementation. It matches most of the document, supports balance, and preserves the classic crawler resource feel.

### 2.2 Resurrection formula conflict
The document references both:
- **25% base** resurrection failure, and
- **20% base** failure reduced by Constitution.

**Recommendation:**
Use **20% - CON%, minimum 1%**. This is the most explicit final formula in the README.

### 2.3 Lockpicking conflict
One section implies lockpicking is available to any character with tools; another says **only Shadowman** can open locks and remove traps.

**Recommendation:**
Make **Shadowman the default lock/trap specialist**, while allowing limited bypass via:
- utility spells like **Knock** / **Find Traps**
- specific items such as skeleton keys or trap kits

### 2.4 Death vs death saves conflict
One section says **0 HP = immediate death**. Another references a **first death save**.

**Recommendation:**
Keep **0 HP = death immediately** for the classic high-stakes tone. Remove death saves from the design unless intentionally added later.

### 2.5 Attribute naming inconsistency
The README mixes:
- Dexterity / Agility
- Wisdom / Piety
- Intelligence / Intellect
- Charisma / Personality

**Recommendation:**
Use a single canonical stat schema everywhere:
- STR, AGI, CON, INT, PIE, PRE, LCK

### 2.6 Warden casting stat inconsistency
The Warden is described with both **INT** and **PIE** associations.

**Recommendation:**
Decide now whether Warden is:
- a **PIE-based ranger** (most consistent with 5E/Wisdom lineage), or
- an **INT-based scout caster** (more unique, but less standard).

### 2.7 Combat presentation inconsistency
One section mentions a **20x20 combat grid**, while almost all combat rules use the **4-rank tactical axis**.

**Recommendation:**
Treat the 4-rank system as canonical. The 20x20 reference should be removed or ignored.

---

## 3. Production Strategy

Build Umberhold in **three concentric rings**:

### Ring 1: Core engine
Prove the game is fun with:
- one explorable 26x26 map
- one town hub screen
- one combat system implementation
- a few monsters, items, classes, and spells

### Ring 2: Vertical slice
Ship a polished slice of the opening game:
- Umberhold village
- Gravenhollow Manor floor 1
- 2-3 quests
- 1 boss
- 1 save/load loop
- working economy, resurrection, and itemization

### Ring 3: Full production
Expand into:
- multiple regions
- full class/race roster
- content-heavy progression
- narrative flags across all regions
- balancing and polish

---

## 4. Recommended MVP Scope

To avoid overbuilding, the first playable version should include only the minimum needed to validate the game loop.

### Exploration MVP
- 1 region: **Umberhold / Gravenhollow Manor**
- 1 full **26x26** map
- step forward/back + turn left/right
- walls, doors, interactables, stairs, one transit point
- minimap/auto-map
- random encounter chance
- 3-5 fixed trigger events

### Combat MVP
- party front/rear ranks
- enemy front/rear ranks
- enemy slot sizes: medium, large, huge
- range checks 1-3
- initiative order
- attack, cast, use item, defend/dodge
- enemy AI with **Advance** for melee units

### Character MVP
- 3 classes: **Man-at-Arms, Shadowman, Friar**
- 3 races: **Human, Stoutling, Hillkin**
- level cap temporarily set to **3-5** during vertical slice
- basic equipment, HP, AC, stats, encumbrance

### Content MVP
- 8-12 monsters
- 20-30 items
- 10-15 spells/abilities
- 1 mini-boss
- 1 boss

### Town MVP
- Inn: rest, save, roster management
- Shop: buy/sell/identify
- Chantry: heal/resurrect
- Quest desk: 2-3 quests

This is enough to prove the core loop: **Explore -> Fight -> Loot -> Return -> Upgrade -> Save**.

---

## 5. Core Game Architecture

The project should be built as a **data-driven RPG framework**, not as hardcoded scene logic.

### 5.1 Main runtime states
Implement a top-level state machine:
- `STATE_TITLE`
- `STATE_TOWN`
- `STATE_EXPLORE`
- `STATE_COMBAT`
- `STATE_DIALOGUE`
- `STATE_MENU`
- `STATE_CHEST`
- `STATE_GRAVEYARD`

The README explicitly requires at least:
- `STATE_EXPLORE`
- `STATE_COMBAT`
- `STATE_DIALOGUE`

### 5.2 Core systems
Plan the codebase around these systems:
- **Game State Manager**
- **Save/Load Manager**
- **Map/Grid System**
- **Encounter System**
- **Combat System**
- **AI System**
- **Character/Party System**
- **Inventory & Equipment System**
- **Spell/Ability System**
- **Narrative Flag System**
- **UI System**
- **Audio/Feedback System**
- **Content Database / Data Loader**

### 5.3 Data-first design
Use JSON, YAML, or similar external files for:
- regions
- tiles
- encounters
- monsters
- items
- spells
- races
- classes
- vocations
- NPC dialogue
- quests
- shop inventories
- day phases and shop schedules
- narrative flags and conditions

This is essential because Umberhold is content-heavy.

---

## 6. Proposed Data Model

### 6.1 Tile schema
Each grid coordinate should map to a tile object like:

```json
{
  "coord": "A1",
  "is_wall": false,
  "texture_id": "manor_stone_01",
  "height": 0,
  "tags": ["interior", "safe"],
  "on_step_trigger": "evt_gravenhollow_entry",
  "interact_id": null,
  "encounter_table": "manor_floor_1_random"
}
```

### 6.2 Monster schema
The README explicitly asks for monster data including slot size, primary range, and 5E stats.

```json
{
  "id": "grave_thrall",
  "name": "Grave Thrall",
  "slot_size": 1,
  "rank_preference": "front",
  "behavior_tags": ["melee", "advance"],
  "primary_range": 1,
  "level": 1,
  "xp_value": 50,
  "5e_stats": {
    "str": 12,
    "agi": 10,
    "con": 12,
    "int": 3,
    "pie": 6,
    "pre": 5,
    "lck": 0,
    "ac": 11,
    "hp": 9,
    "proficiency": 2,
    "attack_bonus": 3,
    "damage": "1d6+1"
  },
  "resistances": [],
  "immunities": [],
  "loot_table": "undead_common",
  "ai_profile": "melee_basic"
}
```

### 6.3 Narrative flag schema
Use global flags with simple condition evaluation.

```json
{
  "gravenhollow_gate_open": true,
  "villager_marta_rescued": false,
  "boss_crypt_warden_defeated": false,
  "chantry_intro_seen": true
}
```

### 6.4 Encounter schema
Separate **random** and **fixed** encounters.

```json
{
  "id": "manor_floor_1_random",
  "type": "random_table",
  "entries": [
    { "monster_group": "2x_grave_thrall", "weight": 50 },
    { "monster_group": "1x_bone_hound", "weight": 25 },
    { "monster_group": "1x_thrall_1x_acolyte", "weight": 25 }
  ]
}
```

---

## 7. Exploration System Plan

### Goals
Deliver a satisfying first-person dungeon-crawl feel before adding a lot of content.

### Features
- 90-degree turning
- forward/backward stepping
- collision against walls
- interactable doors and triggers
- coordinate-based map logic (`A1` to `Z26`)
- first-person rendering with wall textures and simple props
- minimap / automap
- random encounter roll on step
- fixed encounters and narrative triggers by coordinate
- transit coordinates between maps

### Technical notes
- Keep map logic strictly grid-based even if rendered in 3D.
- Store player position as `{x, y, facing}`.
- Build encounters and triggers off coordinates, not world-space physics.
- Support quick authoring tools for designers to place walls, encounters, and triggers.

### Deliverable
A player can walk through Gravenhollow Manor, turn corners, trigger events, find loot, and enter combat.

---

## 8. Combat System Plan

### Battlefield model
Use the canonical 4-rank axis:
- Party Rear
- Party Front
- Enemy Front
- Enemy Rear

### Core rules to implement first
1. initiative order
2. target selection
3. range validation
4. hit/miss and damage resolution
5. death handling
6. enemy advance logic
7. victory/defeat flow

### Enemy slot logic
- Enemy front rank max slots: 6
- Enemy rear rank max slots: 6
- Size costs:
  - Medium: 1
  - Large: 2
  - Huge: 3
  - Gigantic: 4

### Advance algorithm
At end of enemy turn or round:
- if front rank has open slots
- and a rear-rank enemy has `melee`/`advance` behavior
- and its size fits the available slots
- move it forward

### Range model
Implement a `RangeCheck(attacker_rank, target_rank, range_value)` helper.

Suggested rank distances:
- adjacent rank = 1
- one rank gap = 2
- two rank gap = 3

### Combat UI MVP
- action menu
- spell list
- enemy portraits in slot order
- hover/select target feedback
- invalid range messaging
- turn order strip
- status icons
- damage/heal popups

### Deliverable
Combat is tactically readable, fast, and faithful to the README before advanced class abilities are added.

---

## 9. Character System Plan

### Character creation
Implement in layers.

#### Phase 1
- name
- sex
- race
- class
- rolled stats
- starting HP
- starting gold

#### Phase 2
- vocation/background perks
- portrait selection
- starting gear packages
- reroll/keep/discard flow

### Canonical stats
- Strength
- Agility
- Constitution
- Intellect
- Piety
- Personality
- Luck

### Party rules
- up to 6 characters
- front/rear placement
- dead characters moved to rear and marked visually
- inn roster management

### Progression plan
Start with a reduced vertical-slice cap, then expand to 10.

Implement:
- XP gain
- level-up tables
- HP growth
- class features
- spell progression
- equipment restrictions

### Deliverable
A player can create a party, equip them, level them, and feel meaningful class differences.

---

## 10. Item, Economy, and Inventory Plan

### Must-have systems
- equipment slots / paper doll
- inventory capacity by weight
- no stacking
- trade between party members
- item identification
- shop buy/sell flow
- gold economy

### Initial item categories
- weapons
- armor
- shields
- consumables
- utility items
- quest items
- magical gear

### Balance guidance
Because resurrection, identification, and recovery all cost money, the economy should be tuned around:
- survival pressure
- gear improvement
- attrition over long excursions

### Deliverable
Loot matters, capacity matters, and returning to town feels strategically necessary.

---

## 11. Spell and Ability Plan

### First implementation pass
Only ship enough spells to prove the system:
- direct damage
- healing
- buff
- debuff
- utility
- control

### MVP spell shortlist
- Cure Light Wounds
- Arcbolt
- Shockwave
- Light
- Witchlight
- Sleep
- Beguile
- Sure Strike
- Identify

### Ability rollout
Start with a limited subset of class-defining abilities.

Recommended early abilities:
- Shadowman: Open Locks, Find/Remove Traps, Low Blow
- Man-at-Arms: basic frontline passives
- Friar: healing and anti-undead utility

### Deliverable
Magic and class identity are present early, but system complexity stays manageable.

---

## 12. Narrative and Quest Plan

### Narrative structure
The README supports a layered narrative model:
- town dialogue
- fixed set-piece encounters
- rescue and recovery goals
- region progression
- global threat escalation

### Narrative system requirements
- global story flags
- coordinate-based set pieces
- NPC conditional dialogue
- quest states
- boss defeat flags
- shop/service unlocks based on progress

### Vertical slice story content
Use only the opening act:
- disappearances in Umberhold
- entry into Gravenhollow Manor
- rescue one or more villagers
- reveal manor as a conduit of necromantic power
- defeat first boss

### Deliverable
Players understand why they are exploring, not just what they are killing.

---

## 13. UI/UX Plan

### Core screens
- title screen
- party creation
- village hub / town menu
- explore HUD
- combat HUD
- chest/loot UI
- inventory/equipment UI
- spell UI
- shop UI
- graveyard screen

### Explore HUD
- compass/facing
- coordinate display
- minimap
- party status
- active buffs
- contextual interaction prompt

### Combat HUD
- initiative strip
- action menu
- enemy formation display
- range validation feedback
- portraits/status effects
- combat log

### Goal
The UI must make the unusual combat model instantly readable.

---

## 14. Audio, VFX, and Feel Plan

The README emphasizes emotional contrast: dread during risk, relief on survival.

### Priority feedback features
- heavy weapon impact sounds
- spell cast audio identity
- hit/miss/dodge feedback
- target selection sounds
- party death portrait swap
- graveyard transition
- ambient dungeon audio
- village safety audio contrast

### Visual priorities
- readable enemy slots and rank separation
- strong status effect indicators
- blood/impact overlays used sparingly but effectively
- atmospheric first-person environments over high-poly complexity

### Deliverable
The game feels tense even before content volume is high.

---

## 15. Save/Load Plan

### Rules
- manual saves only at inns
- no mid-dungeon save
- total wipe returns to graveyard screen
- load returns to last inn save

### Technical requirements
- save party roster
- save inventory and gold
- save quest and narrative flags
- save defeated fixed encounters
- save discovered map state if desired
- save current region/town state

### Recommendation
Keep random encounter states unsaved; keep fixed/narrative states persistent.

---

## 16. Recommended Build Order

## Phase 0 - Preproduction
- finalize canonical rules
- choose engine and rendering approach
- define art style target
- create technical spike for grid movement + 1st-person walls
- lock data schemas

## Phase 1 - Core exploration prototype
- 26x26 grid loader
- first-person movement
- turning
- wall rendering
- triggers
- random encounter handoff

## Phase 2 - Combat prototype
- rank system
- slots and monster sizes
- action targeting
- range checks
- enemy AI advance
- victory/defeat loop

## Phase 3 - Character and inventory prototype
- party data
- items/equipment
- stat calculations
- XP/levels
- basic spells

## Phase 4 - Town loop prototype
- inn
- shop
- chantry
- quest board
- save/load

## Phase 5 - Vertical slice content
- Gravenhollow Manor map
- opening quests
- first monster roster
- first boss
- itemization pass
- dialogue and flags

## Phase 6 - Polish and balancing
- onboarding
- UI cleanup
- economy tuning
- encounter tuning
- resurrection tuning
- bug fixing

## Phase 7 - Full game expansion
- additional regions
- more classes/races
- more spells and bosses
- narrative branching and late-game balancing

---

## 17. Suggested Milestones

### Milestone A - Movement Box
**Success criteria:**
- player moves and turns in a textured 3D grid
- coordinates display correctly
- walls block movement

### Milestone B - First Combat
**Success criteria:**
- random encounter starts from exploration
- one party action and one enemy action resolve correctly
- range rules work

### Milestone C - First Loop
**Success criteria:**
- player explores, fights, loots, returns to town, rests, saves

### Milestone D - Vertical Slice
**Success criteria:**
- full 30-60 minute playable opening segment
- at least one set-piece boss encounter
- functioning progression and town services

### Milestone E - Content Pipeline Ready
**Success criteria:**
- designers can add maps, monsters, items, and encounters without code changes

---

## 18. Biggest Risks

### Scope risk
The README describes enough content for a full RPG. Without an MVP boundary, the project can balloon quickly.

### Content-authoring risk
A 9-region game with classes, spells, races, bosses, and dialogue will live or die by pipeline quality.

### Balance risk
The combination of:
- six-character parties
- resurrection failure
- inn-only saves
- slower XP
- gear dependency

can become punishing in a way that feels unfair if not carefully tuned.

### UI clarity risk
The rank/slot system is novel enough that weak UI could make combat feel confusing.

### Recommendation
Do not build all content first. Prove clarity and tension in a small opening slice.

---

## 19. Immediate Next Steps

1. Create a **canonical design doc** that resolves all contradictions listed above.
2. Choose engine/tech stack.
3. Build a **movement prototype** in a single 26x26 test map.
4. Implement a **combat prototype** with 3 player classes and 4-5 monsters.
5. Create the **data schema files** for tiles, monsters, items, spells, and encounters.
6. Build the **town loop** with inn/save, shop, and resurrection.
7. Produce a **Gravenhollow vertical slice** before expanding to more regions.

---

## 20. Recommended Definition of Done for Version 0.1

Version 0.1 should be considered successful when a player can:
- create a party
- walk a 3D 26x26 map in first person
- trigger random and fixed encounters
- fight using the 4-rank / 6-slot combat rules
- loot and equip items
- return to Umberhold
- heal, resurrect, rest, and save at the inn
- complete the first major manor objective

That version will prove the game's identity and provide a solid base for full production.

---

## Final Recommendation

**Do not start by building all nine regions.**

Start by making **Gravenhollow Manor** excellent. If the opening village, the first dungeon grid, and the first boss are atmospheric and mechanically sharp, the rest of Umberhold can scale from a strong foundation.
