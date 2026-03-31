# Umberhold Deep Gap Analysis

## Purpose
This document analyzes the gap between the current `README.md` vision and what is required to build a shippable **grid-based 3D RPG**.

This is not a critique of the concept. The concept is strong.

The issue is that the current material is still closer to a **creative design brief** than a **production-ready game specification**. The biggest gaps are not imagination; they are **canon, systems closure, content definition, tooling, and scope control**.

---

## Executive Summary

### Overall assessment
**Umberhold has a compelling identity but is not yet production-ready.**

The current design is strongest in:
- tone and atmosphere
- macro gameplay loop
- combat fantasy
- town/crawl tension
- setting premise

The current design is weakest in:
- canonical rules consistency
- low-level combat rules
- player party formation rules
- progression math and balance tables
- content pipeline definition
- technical/tooling requirements
- scope realism for a first implementation

### Core conclusion
Before building a full game, Umberhold needs a **Canon Pass** and a **Vertical Slice Spec**.

Without those two steps, implementation risk is high because different parts of the README currently imply different games.

---

## Readiness Snapshot

| Area | Readiness | Notes |
|---|---:|---|
| Fantasy / tone / hook | 9/10 | Very strong and distinctive |
| Core loop concept | 8/10 | Clear and appealing |
| Exploration concept | 6/10 | Strong direction, missing implementation rules |
| Combat concept | 7/10 | Strong identity, missing resolution detail |
| Character system | 5/10 | Interesting classes/races, many unresolved mechanics |
| Economy / progression | 4/10 | Broad intent exists, math does not |
| Narrative structure | 6/10 | Good premise, little quest implementation detail |
| UI / UX definition | 5/10 | Basic input idea exists, flow clarity incomplete |
| Technical architecture | 3/10 | Almost entirely absent |
| Content authoring pipeline | 2/10 | Not yet defined |
| Production scope control | 2/10 | Current scope is much larger than MVP |
| Commercial/legal readiness | 3/10 | 5E usage needs review |

---

## 1. Vision-Level Gaps

## 1.1 The project is defined emotionally, not operationally
The README does an excellent job describing:
- what the game should feel like
- what the player fears
- what the player wants
- what games it is inspired by

But it does a weaker job defining:
- exact gameplay rules
- how systems interact when edge cases occur
- what content is required for version 0.1, 0.5, and 1.0
- what the minimum fun version is

### Why this matters
A mood-driven document is great for alignment, but engineers and content designers need a rule-driven one.

### Gap
There is no single source of truth for:
- canonical mechanics
- out-of-scope features
- temporary vertical-slice simplifications
- priority order between systems

### Recommendation
Create two documents before major implementation:
1. **canon.md** — final authoritative rules
2. **slice.md** — exact scope for the first playable vertical slice

---

## 1.2 The game has full-RPG scope but prototype-level definition
The README implies:
- 9 regions
- multiple towns and dungeons
- 7 classes
- 6 races
- vocation/background system
- many spells
- extensive itemization
- cutscene set pieces
- lock/trap/chest systems
- resurrection economy
- full save/load structure
- first-person 3D exploration
- bespoke rank combat

### Why this matters
This is a **full game production scope**, not a prototype scope.

### Gap
The design breadth currently exceeds the definition depth.

### Recommendation
Lock a brutal MVP:
- 1 town
- 1 dungeon
- 3 classes
- 3 races
- 8-12 monsters
- 20-30 items
- 10-15 spells/abilities
- 1 boss

---

## 2. Canon and Consistency Gaps

This is the single biggest blocker category.

## 2.1 Magic system contradiction
The README says both:
- spellcasters use **5E spell slots**
- there are **no spell slots**, only spells and doubled cast counts

It also later says:
- cantrips are free
- spell save DC follows a 5E-style formula

### Why this matters
Magic affects:
- balance
- attrition
- UI
- save-state data
- class identity
- dungeon pacing

### Gap
There is no canonical answer to:
- slots vs spell charges vs casts-per-level
- prepared vs known spells
- how many spells are learned at each level
- whether out-of-combat spells consume the same resource as combat spells

### Recommendation
Define one final magic model with examples for levels 1, 5, and 10.

---

## 2.2 Resurrection contradiction
The README references both:
- 25% base resurrection failure
- 20% base resurrection failure reduced by Constitution

### Gap
The project currently has two resurrection systems.

### Why this matters
Resurrection odds are central to the game's emotional loop. Small percentage differences have huge psychological impact.

### Recommendation
Make one formula canonical and use it everywhere:
- README
- town services
- UI
- economy balancing
- tutorial text

---

## 2.3 Death-state contradiction
The design says:
- 0 HP = death immediately
- graveyard on total wipe
- resurrection via Chantry

But it also references:
- a first death save in one section

### Gap
The game does not currently have a single, final mortality model.

### Recommendation
Pick one:
- **Classic mode:** 0 HP = dead immediately
- **Soft mode:** downed state / death saves

For Umberhold's intended tone, classic mode is more coherent.

---

## 2.4 Lockpicking contradiction
The chest section implies a more general skill-check approach, while the class section says only **Shadowman** opens locks and finds/removes traps.

### Gap
The player-facing rules for lock and trap interaction are not canonized.

### Missing decisions
- Can non-Shadowmen attempt locks with tools?
- Can any class examine traps?
- Do spells replace class skill checks or just assist them?
- Are jammed locks character-specific or globally jammed?

---

## 2.5 Attribute naming inconsistency
The document alternates between 5E names and Umberhold names.

Examples:
- Dexterity vs Agility
- Intelligence vs Intellect
- Wisdom vs Piety
- Charisma vs Personality

### Gap
This leaks into:
- saving throw labels
- spells
- class descriptions
- race traits
- equipment formulas

### Recommendation
Adopt one single internal naming scheme and ban mixed usage in data/content.

---

## 2.6 Warden stat inconsistency
The Warden is associated with both **INT** and **PIE** in different places.

### Why this matters
This affects:
- spell DCs
- equipment priorities
- level-up curves
- class identity

### Recommendation
Resolve now, before item and spell data are authored.

---

## 2.7 4-rank axis vs 20x20 combat grid contradiction
One loot section references a **20x20 combat grid** dissolving into a chest screen. Nearly all other combat content assumes a **4-rank battlefield**.

### Recommendation
Delete all references to a 20x20 combat grid unless a second combat mode is actually intended.

---

## 2.8 Saving / consequence contradiction
The game says:
- death can be permanent if resurrection fails
- total defeat reloads from last inn save
- no permanent penalties if player reloads

### Gap
The actual consequence model is unclear.

### Open questions
- Can a player accept a failed resurrection and continue with a five-person roster?
- Is reloading always allowed without friction?
- Is permadeath a real system or a soft fiction because reload nullifies it?
- Is there any anti-save-scum design?

### Recommendation
State plainly whether the intended experience is:
- **true persistent consequence**, or
- **high tension but recoverable through load**

---

## 3. Exploration System Gaps

## 3.1 The grid exists conceptually, not authorably
The 26x26 coordinate system is clear at a high level, but content production details are absent.

### Missing pieces
- exact map file format
- coordinate indexing rules
- how transit coordinates are linked between regions
- how secret doors are stored
- whether ceilings/floors vary by tile
- whether props occupy tiles or are cosmetic
- whether doors are tiles, overlays, or entities
- whether events fire once, always, or conditionally

### Why this matters
A map system is not complete until a designer can reliably author it without bespoke code support.

### Recommendation
Define a full map schema and a map-editing workflow.

---

## 3.2 First-person rendering style is undefined
The design says **1st-person 3D**, but not:
- raycast retro style
- low-poly full 3D
- billboard enemies
- fixed camera depth budget
- how interactables are represented

### Gap
The rendering approach strongly affects:
- engineering effort
- asset budget
- performance
- readability
- atmosphere

### Recommendation
Lock an art/tech rendering model before building the map pipeline.

---

## 3.3 Movement rules are underdefined
You have WASD and 90-degree turning, but not:
- whether backward movement is allowed or slower
- whether strafing exists
- whether some tiles alter move cost or trigger checks
- whether turning can trigger encounters
- whether environmental hazards damage on entry, per step, or per turn

### Recommendation
Create a one-page movement rules spec with all edge cases.

---

## 3.4 Encounter triggering lacks formula closure
The README says random encounters trigger by percentage chance during movement.

### Missing decisions
- flat rate or region-specific curve
- safe tiles / no-encounter zones
- encounter cooldown after battle
- anti-frustration rules
- whether facing, tile tags, or time affect rates
- whether set-piece coordinates suppress random battles

### Recommendation
Define encounter pacing mathematically.

---

## 3.5 Mapping and navigation support are implied, not specified
Classic crawlers live or die by map legibility.

### Missing decisions
- automap or manual map or both
- fog of war behavior
- whether special tiles annotate automatically
- note-taking support
- orientation display in HUD
- accessibility options for players prone to first-person disorientation

---

## 4. Combat System Gaps

The combat concept is strong, but the resolution layer is incomplete.

## 4.1 Party formation rules are missing
The enemy formation has explicit slot rules. The party formation does not.

### Critical open questions
- How many party members can stand in the front rank?
- Is it always 3 front / 3 rear?
- Are there party-side slot sizes, or only enemy-side slot sizes?
- If Hillkin are Large, do they occupy more front-rank capacity?
- Can the player reorder ranks in combat or only outside combat?
- If a front-rank ally dies, does a rear ally auto-step forward?

### Why this matters
This is a blocker. The player formation is a core combat rule and currently undefined.

### Recommendation
Define party rank occupancy explicitly before any real combat implementation.

---

## 4.2 Range model exists, but targeting geometry does not
Range 1-3 is defined by rank distance, but the game also references:
- enemy portraits within 6-slot ranks
- spells hitting adjacent enemies in the same rank

### Missing decisions
- Do enemies have horizontal slot indices from 1-6?
- Can a Large/Huge enemy occupy contiguous slots?
- What counts as "either side" of a Huge enemy?
- Can a spell target the center slot of a 3-slot enemy?
- How is targeting handled if the enemy formation has gaps?

### Recommendation
Formalize targeting as both:
- **rank distance**, and
- **slot geometry**

---

## 4.3 Action economy is unclear
The README shows dropdowns for:
- Attack
- Cast Spell
- Use Item
- Dodge
- Equip Another Weapon

But it does not define:
- whether each turn allows one action only
- whether bonus actions exist
- whether reactions exist
- whether weapon swapping consumes a turn
- whether class features like Dual Wield require a bonus action
- how readying, guarding, or fleeing work

### Recommendation
Write a strict turn economy ruleset.

---

## 4.4 Hit resolution math is missing
There are weapon stats, armor stats, and 5E references, but the game's actual combat formula is incomplete.

### Missing formulas
- attack roll formula
- initiative roll formula
- crit rules for all classes, not just Shadowman
- off-hand damage rules
- shield stacking rules
- spell hit vs save distinction
- status effect duration bookkeeping
- enemy proficiency scaling

### Why this matters
You cannot balance combat until the formulas are final.

---

## 4.5 AI definition is too shallow for production
Current AI notes are directionally good:
- melee advances
- ranged often stays rear

But not enough for implementation.

### Missing AI rules
- target selection priorities
- focus-fire behavior
- healing/self-preservation logic
- retreat behavior
- summon behavior
- boss scripting layers
- reaction to status effects
- whether rear ranged enemies move forward if front rank is empty and they are out of valid targets
- whether giant monsters can block advancement paths

### Recommendation
Create AI profiles and decision trees, not just descriptive behavior labels.

---

## 4.6 Status effect system is incomplete
The README references conditions like:
- poisoned
- charmed
- blinded
- frightened
- sleep
- bleeding

### Missing decisions
- full condition list
- stacking rules
- duration timing rules
- cleanse rules
- death interaction rules
- immunity/resistance taxonomy

### Recommendation
Define a canonical status library and timing model.

---

## 4.7 Boss encounter scripting is underspecified
The design promises story-heavy boss fights, but not:
- phase changes
- unique mechanics framework
- pre-fight dialogue triggers
- boss defeat scripting hooks
- boss-specific resistances or immunities

### Gap
Bosses exist as intention, not system.

---

## 5. Character System Gaps

## 5.1 Party creation flow is flavorful but not system-complete
The character creation sequence includes:
- sex
- race
- vocation
- stat rolls
- HP
- starting gold
- keep/discard
- class
- name

### Missing decisions
- can class be chosen before stat roll preview?
- are there class stat minimums?
- are race/class restrictions allowed?
- what happens if a generated character is unusable?
- can the player reroll infinitely?
- are portraits/class visuals tied to race/sex/class combinations?

---

## 5.2 Class definitions are incomplete
A full class lineup exists, but only Shadowman receives detailed level progression.

### Missing class content for most classes
- level 1-10 feature tables
- subclass/no-subclass decision
- spell progression and spell access
- weapon/armor proficiencies
- class resource rules if any
- late-game power identity

### Gap severity
**Critical.** Combat and progression cannot be balanced while six of seven classes are underspecified.

---

## 5.3 Vocation system now has canon boons, but implementation details remain
Vocations are now defined as passive character-creation backgrounds with always-on Boons and hidden exact mechanics.

### Canon decisions now set
- vocation is chosen at character creation
- the Boon is passive, always active, and cannot be changed
- players see a flavor hint, not the exact rules text, during character creation
- no vocation-specific dialogue or quest branching exists in the vertical slice

### Remaining integration questions
- Can two systems grant overlapping immunities?
- Is vocation visible in UI after creation?
- How, if at all, should hidden Boons be surfaced later in play?
- Are vocations balanced against each other or mostly flavor?

---

## 5.4 Luck is underdesigned
Luck is listed as a core stat but has very few explicit hooks.

### Problem
A stat that rarely matters becomes a trap stat unless carefully integrated.

### Missing hooks
- crit chance
- trap avoidance
- rare loot chance
- resurrection modifier?
- initiative ties?
- status resistance?

### Recommendation
Either deeply integrate Luck or remove it.

---

## 5.5 Size system and player races are not reconciled
Races include:
- Small
- Medium
- Large

But the implications of player size are unclear.

### Missing decisions
- Does size affect party rank capacity?
- Can Large characters use all equipment?
- Do Small characters have front-rank restrictions?
- Does size alter hit chance or cover?
- Does a Large Hillkin need special armor sizing and higher costs?

### Recommendation
Do not keep size tags unless they have actual systemic meaning.

---

## 5.6 Ability score growth is unclear
The Shadowman table references **Uncapped Attribute Growth**. Human says **+1 to four random stats (max 18)**.

### Missing decisions
- normal stat cap
- post-level cap behavior
- whether items can push beyond cap
- whether race bonuses apply before or after rolling
- what "uncapped" specifically permits

---

## 6. Economy, Loot, and Progression Gaps

## 6.1 XP pacing is stated, not tabled
The README says leveling requires **5x standard 5E XP**, but no full table is given.

### Missing pieces
- exact XP thresholds for levels 1-10
- XP rewards by encounter difficulty
- XP split rules across party members
- scaling for dead or benched members

---

## 6.2 Encumbrance system lacks formula clarity
The design strongly emphasizes restrictive inventory, but not:
- carry capacity formula
- how equipped weight counts
- whether strength modifies carry cap linearly or by tier
- whether dead characters still carry gear weight normally
- whether containers exist

### Recommendation
Write the exact carry formula and UI behavior when over limit.

---

## 6.3 Shop economy is incomplete
There are named vendors and broad services, but not:
- starting inventories
- rest costs
- identify costs
- potion pricing balance
- resale rates
- inventory refresh rules
- region-specific price inflation

### Why this matters
Economy is central because resurrection and healing costs create pressure.

---

## 6.4 Loot tables are missing
The design mentions uncommon/rare magic items and coordinate-based rewards.

### Missing content structure
- region loot tables
- chest reward tables
- boss unique rewards
- identified vs unidentified drop rules
- cursed item rules if any

---

## 6.5 Ammunition and consumable persistence are unclear
The game lists bows and crossbows, but not:
- whether arrows/bolts are tracked
- whether quivers exist
- whether ammo can be recovered
- whether thrown weapons are retrievable

Given the no-stacking rule, this matters a lot.

---

## 7. Narrative and Content Gaps

## 7.1 Main quest structure exists only at the macro level
The premise is strong, but the actual playable story structure is not defined in enough detail.

### Missing content definitions
- region-by-region plot beats
- quest dependency graph
- key NPC arc summaries
- mandatory vs optional side quests
- fail states for rescues or timed story beats
- exact reveal cadence for the Lich King threat

---

## 7.2 Set-piece framework is conceptually present, not authorable
Set-piece encounters are central to Umberhold's identity.

### Missing decisions
- event scripting format
- dialogue trigger system
- camera control / presentation rules
- conditional branching syntax
- quest update hooks
- whether set pieces can include noncombat resolutions

---

## 7.3 Intelligent NPC claim is underspecified
The README says NPCs have their own intelligence and react to progression.

### Gap
That is a product promise, not a spec.

### Missing decisions
- authored dialogue trees vs procedural text
- daily schedule or static state
- memory model
- quest gating logic
- how much reactivity is realistic for production

### Recommendation
Downscope the phrase "intelligent NPCs" into concrete dialogue-state behavior.

---

## 7.4 Regional content burden is enormous
The world structure implies:
- 9 regions
- each with town + dungeon + regional grid
- multiple bosses and side quests

### Gap
The content budget is not yet acknowledged operationally.

### Recommendation
Estimate asset and writing counts before committing to all 9 regions.

---

## 8. UI/UX Gaps

## 8.1 Input scheme exists, but interface flow does not
The README says:
- WASD movement
- A/C for attack/cast
- left-click targeting
- dropdowns for actions

### Missing UX details
- how a turn begins visually
- how invalid targets are signaled
- whether keyboard-only control is possible
- whether enemy slots highlight valid targets by range
- whether right-click cancels a pending action
- whether recent spells are pinned per character or globally

---

## 8.2 Combat readability is at risk
The combat model has unusual geometry:
- 4 ranks
- 6 horizontal enemy slots
- ranged restrictions
- large enemies spanning multiple slots

### Gap
Without excellent UI, players may not understand why they can or cannot hit a target.

### Recommendation
The UI must explicitly show:
- slot occupancy
- targetability
- blocked states
- range reason text
- expected hit chance or at least attack preview

---

## 8.3 First-person exploration comfort is not addressed
Grid crawlers are less demanding than free-look first-person games, but comfort still matters.

### Missing accessibility choices
- camera bob toggle
- turn animation speed / snap-turn option
- font scaling
- subtitle and combat log readability
- colorblind-safe status effects
- key rebinding
- controller support or deliberate non-support

---

## 9. Technical Architecture Gaps

## 9.1 Engine choice is not stated
This is a major gap because first-person 3D + turn-based tactical UI can be built in many ways, but tooling and pipeline decisions depend on the engine.

### Missing decision
- Unity / Godot / Unreal / custom / web?

### Why this matters
Engine choice affects:
- rendering method
- UI stack
- save system
- data loading
- moddability
- build targets
- staffing feasibility

---

## 9.2 Data pipeline is not defined
The game clearly wants data-driven content, but does not define:
- file format
- validation rules
- hot reload support
- localization support
- content references / IDs
- schema versioning

### Recommendation
Define canonical content schemas early and validate them automatically.

---

## 9.3 Tooling requirement is missing
A game with 26x26 maps, flags, encounters, item databases, and scripted events needs tools.

### Missing tool plan
- map editor or importer
- encounter editor
- dialogue editor
- loot table validator
- content linting
- save inspector/debug tools

### Gap severity
**Critical for production efficiency.**

---

## 9.4 Save system design is incomplete
Inn-only saving is a design pillar, but save architecture is not defined.

### Missing decisions
- single save or multiple slots
- autosave in town or not
- save on rest or manual only
- what data is persisted after leaving a dungeon mid-run
- whether chest states persist immediately or only on save
- how dead/benched roster members are serialized

---

## 9.5 Testing strategy is absent
This project needs both automated and manual validation.

### High-risk systems for testing
- range validation
- enemy advance logic
- size/slot occupancy
- resurrection probability
- encumbrance edge cases
- save/load integrity
- flag-based set pieces

### Recommendation
Build simulation tests for combat math and state transitions early.

---

## 10. Content Production Gaps

## 10.1 Asset count is not budgeted
To ship even a modest vertical slice, you need:
- wall/floor/ceiling sets
- props
- UI icons
- character portraits
- enemy portraits
- spell FX
- hit effects
- audio cues
- music / ambient loops
- town service screens
- chest artwork

### Gap
No asset list, style guide, or production budget exists.

---

## 10.2 Monster roster is underdefined operationally
You have conceptual enemy roles, but not enough finished data.

### Missing per-monster data
- initiative modifier
- full attack list
- behavior script/profile
- resistances/immunities
- loot table
- portrait/art requirements
- sound set
- death behavior

---

## 10.3 Spell list is incomplete relative to class spread
There is a good starting list, but not enough to support all casting classes across 10 levels.

### Gap
Spell coverage for:
- Friar
- Crusader
- Warden
- Troubadour
- Hedge Wizard

is not yet defined as a production library with progression and balance.

---

## 11. Balance Gaps

## 11.1 The tension loop is clear, but the tuning model is not
The emotional design depends on a careful balance between:
- attrition
- resurrection risk
- save restriction
- encounter rate
- XP gain
- gold income
- item drop quality
- healing availability

### Gap
There is no balancing framework showing how these systems interact over a typical 30-minute, 1-hour, and 3-hour expedition.

### Recommendation
Create a **run economy model**:
- expected encounters per trip
- expected damage taken
- expected consumables spent
- expected gold gained
- expected chance of a death event

---

## 11.2 Early game may be overly punitive
The design includes:
- 3d6 fixed stat rolls
- inn-only saves
- resurrection failure
- slower-than-5E leveling
- encumbrance pressure
- limited recovery

### Risk
This can create a highly authentic crawler tone, but also a steep frustration wall.

### Gap
There is no onboarding difficulty strategy.

### Recommendation
Design the first dungeon floor specifically as a **learning corridor**, not just a punishing attrition test.

---

## 11.3 Class balance cannot be assessed yet
Without finalized class tables and core formulas, classes cannot be compared.

### Likely balance risks
- Shadowman utility dominance because locks + traps + burst damage are all concentrated in one class
- Friar mandatory status because resurrection/healing pressure may be too high without one
- Hillkin raw survivability overpowering smaller races if size drawbacks are weak
- Troubadour complexity without enough payoff

---

## 12. Scope and Production Gaps

## 12.1 The current full-game scope is very large
Operationally, the project is aiming at something closer to a classic party RPG campaign than a small indie prototype.

### Scope drivers
- 9 regions
- multiple service hubs
- many classes/races/vocations
- custom tactical combat
- significant narrative content
- first-person 3D exploration
- lots of item/spell data

### Gap
There is no staffing or schedule model attached to this ambition.

### Recommendation
Do not estimate the whole game until the vertical slice is fun.

---

## 12.2 No milestone kill criteria are defined
A project with this many systems needs explicit checkpoints.

### Missing criteria
- what proves exploration is fun?
- what proves combat is readable?
- what proves economy pressure is enjoyable rather than oppressive?
- what content count is required before expanding beyond region one?

---

## 13. Legal / Licensing Gap

## 13.1 5E dependency needs legal review
The document repeatedly references **5E D&D** mechanics and equivalents.

### Why this matters
If this is intended to be released commercially, you must ensure that:
- mechanics are used in a legally safe way
- protected expression is not copied
- terminology drawn from SRD/Open Gaming/Creative Commons sources is handled correctly
- non-open content is avoided

### Gap
No legal framing exists yet for how "5E-based" the final implementation will be.

### Recommendation
Do a legal pass early. This is a real blocker if the project is commercial.

---

## 14. Top Blockers Before Serious Production

These are the highest-priority unresolved gaps.

1. **Canonical rules pass**
   - magic model
   - death/resurrection model
   - stat naming
   - save consequence model

2. **Party formation spec**
   - front/rear occupancy
   - player size effects
   - death/replacement behavior

3. **Combat math spec**
   - attack, damage, initiative, crits, durations, action economy

4. **Vertical slice scope lock**
   - exact region/class/monster/item count for first playable

5. **Technical architecture decision**
   - engine, rendering approach, data format, save model

6. **Tooling plan**
   - map authoring, dialogue authoring, validation tools

7. **Progression math**
   - XP table, economy curves, shop prices, encumbrance formula

8. **Class completion**
   - full 1-10 tables for all intended slice classes

9. **Narrative flag system spec**
   - conditions, event scripting, persistence

10. **Legal review of 5E dependency**

---

## 15. Recommended Closure Plan

## Phase A - Canon Pass
Create `canon.md` and resolve every contradiction in the README.

### Required outputs
- final stats list
- final death model
- final resurrection model
- final magic model
- final class terminology
- final combat geometry

---

## Phase B - Combat Closure Pack
Create a combat rules packet containing:
- party formation rules
- enemy formation rules
- slot occupancy diagrams
- attack formula
- initiative formula
- action economy
- status timing
- AI profiles
- example combat transcript

---

## Phase C - Vertical Slice Spec
Define exactly:
- one town
- one dungeon
- one overland approach if needed
- 3 classes
- 3 races
- 10 monsters
- 20 items
- 10 spells
- 3 quests
- 1 mini-boss
- 1 boss

If it is not in this document, it is out of scope.

---

## Phase D - Tooling + Data Spec
Define:
- map schema
- encounter schema
- monster schema
- item schema
- spell schema
- dialogue schema
- save schema

And ideally build validation tooling before large-scale content authoring starts.

---

## 16. Final Judgment

**Umberhold is high-potential, but currently under-specified where it matters most for implementation.**

The concept does not lack personality.
It lacks closure.

The main gap is not "more ideas." The main gap is turning the existing ideas into:
- one canonical rule set
- one manageable first slice
- one data pipeline
- one production plan grounded in actual content cost

If those gaps are closed, the project has a strong foundation.
If they are not, implementation will drift, the UI will become confusing, and the scope will expand faster than the game becomes playable.

---

## Short Version

**Current state:** excellent pitch, partial design, not yet a full spec.

**Most dangerous gaps:**
- contradictory rules
- undefined party formation
- incomplete combat math
- unbounded scope
- missing tooling/data pipeline

**Best next move:**
Do a canon pass, then build a narrow vertical slice around **Umberhold + Gravenhollow Manor**.
