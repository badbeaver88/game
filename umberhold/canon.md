# Umberhold Canon

This document is the current consolidated rules canon for Umberhold.

It combines the currently approved standalone canon sheets into one reference.

This file does **not** modify `MASTER.md`.

---

## 1. Core Combat Flow

When combat begins, the game transitions from exploration to the **combat screen**.

Combatants are placed into the battlefield formation used by Umberhold's tactical combat system.

---

## 2. Initiative

At the start of combat, every combatant rolls initiative.

### Initiative Formula

```text
1d20 + Agility Bonus + other initiative modifiers
```

### Possible Initiative Modifiers
Initiative modifiers may come from:
- class abilities
- magical items
- active spells
- active songs
- other special effects

### Initiative Order
- The combatant with the **highest initiative** acts first.
- All remaining combatants act in descending initiative order.

---

## 3. Initiative Tracker UI

The initiative order is displayed in the **top-left corner** of the combat screen as a vertical list of portraits.

### Display Rules
- The **active combatant** appears at the top.
- The active combatant is highlighted with a **red outline**.
- The **next combatant** appears directly beneath the active one.
- All other combatants follow below in current turn order.

### Rotation Rule
When a combatant finishes their turn:
- they move to the **bottom** of the initiative list
- the next combatant moves to the top
- that combatant becomes the new active turn holder

This creates a clear rotating initiative flow.

---

## 4. Turn Structure

Each combatant takes one **turn** when they reach the top of the initiative order.

On their turn, they may take:
- **one main action**
- **one bonus action**, if they have an ability, attack, spell, or effect that grants one

Umberhold does **not** use reactions.

---

## 5. Main Actions

A combatant may choose **one** of the following main actions on their turn.

### 5.1 Attack
A combatant may perform a physical attack using an equipped weapon.

This may be:
- melee
- ranged
- or other attack forms allowed by abilities or equipment

#### Multiple Attacks
Some characters or monsters may gain more than one attack when taking the Attack action.

**Important rule:**
If the first attack kills the selected target, any remaining attacks are **lost**.
They may **not** be redirected to a different target.

#### Player Targeting Flow
After selecting **Attack**:
- valid enemy targets may be hovered
- the player left-clicks a target
- the attack resolves against that selected target

---

### 5.2 Cast a Spell
Only combatants capable of spellcasting may choose this action.

After selecting a spell:
- beneficial spells may target allies, if the spell allows it
- harmful spells may target enemies, if the spell allows it

Spell range, target rules, and effect resolution must still obey Umberhold's combat and range rules.

---

### 5.3 Use an Item
A combatant may use an item from their inventory, such as:
- a potion
- a curative item
- another usable combat item

Item target and effect rules depend on the item being used.

---

### 5.4 Defend
The **Defend** action represents a full defensive stance.

While defending:
- attacks made against that combatant are made with **disadvantage**
- disadvantage means rolling twice and using the lower result

---

### 5.5 Equip Other Weapon
A combatant may switch to a different weapon.

Rules:
- this consumes the **entire main action**
- the newly equipped weapon cannot be used until the combatant's **next turn**

---

### 5.6 Sing a Song
This action is available only to the **Troubadour**.

A Troubadour may perform a magical song using an instrument.

Songs may provide effects:
- in combat
- out of combat
- to allies
- to enemies
- or to the battlefield state, depending on the specific song

This action should only appear in the combat menu for a Troubadour.

---

## 6. Bonus Actions

A combatant may take **one bonus action per turn**, but only if they have a feature, attack mode, spell, or item effect that specifically allows one.

### Example
- off-hand attack while dual wielding

A combatant does **not** automatically gain a bonus action option every turn. They must have a valid bonus action source.

---

## 7. Reactions

Umberhold does **not** use reactions.

This means:
- no reaction attacks
- no interrupt-style defensive reactions
- no out-of-turn triggered responses unless implemented as a different special mechanic

---

## 8. Combat Interface Flow

The combat interface should support the following turn flow:

1. active combatant is highlighted in the initiative tracker
2. the player selects a main action
3. if needed, the player selects a valid target
4. the action resolves
5. if available, the player may take a bonus action
6. turn ends
7. active combatant rotates to the bottom of the initiative list
8. next combatant becomes active

---

## 9. Damage Types

The current damage types in Umberhold are:

- Slashing
- Piercing
- Bludgeoning
- Fire
- Cold
- Lightning
- Poison
- Acid
- Holy
- Unholy
- Arcane
- Shock
- Falling
- Psychic

---

## 10. Damage Modifiers

### Vulnerability
If a target is vulnerable to a damage type:
- it takes **double damage** from that damage type

### Resistance
If a target is resistant to a damage type:
- it takes **half damage** from that damage type
- always **round down**
- resistance damage can never go below **1 damage** if the attack would otherwise deal damage

### Immunity
If a target is immune to a damage type:
- it takes **no damage** from that damage type

---

## 11. Critical Hits

A critical hit occurs when an attack roll is a **natural 20**.

### Critical Hit Rules
- the natural 20 is checked **before modifiers**
- some features may expand the critical range
- if a feature expands the critical range, it will explicitly say so
- example expanded range: **19-20**

### Critical Damage Rule
On a critical hit:
- **roll all damage dice twice**
- then add any flat bonuses or modifiers

### Example
- Normal hit: `1d8 + 3`
- Critical hit: `2d8 + 3`

---

## 12. Natural 1 Rule

A **natural 1** on an attack roll is always a miss.

This is true regardless of modifiers.

---

## 13. Death Rule

Umberhold does **not** use death saves.

If a character is reduced to **0 or fewer hit points**, they die immediately.

### Immediate Death Rules
- there is no unconscious state
- there is no stabilization state
- there are no recovery rolls
- death happens immediately when current hit points reach `0` or below

### Example
A character with `5 / 40` hit points takes `10` damage.
Their hit points fall below `0`.
They die immediately.

---

## 14. Starting Spell Access

At character creation, spellcasting classes gain access to:
- all cantrips available to their class
- all 1st-level spells available to their class

Cantrips do **not** consume spell slots.

---

## 15. Learning Higher-Level Spells

Higher-level spells are **not** learned automatically in full.

Spells of levels 2-5 must usually be acquired through adventuring, most often in the form of scrolls.

### New Spell Tier Rule
When a caster first gains access to a new spell tier, they immediately learn:
- **one spell** of that newly unlocked level
- chosen from their class spell list

### Example Unlock Pattern
Examples include:
- access to 2nd-level spells at level 3
- access to 3rd-level spells at level 5
- later spell tiers at their normal unlock points

---

## 16. Scrolls, Spellbooks, and Casting Requirements

### Scroll Use
When a scroll is found, a qualified caster may use it in one of two ways.

#### Cast from the Scroll
If the caster meets both:
- the class requirement
- the level requirement

then they may cast the spell directly from the scroll.

Rules:
- the scroll is consumed
- the scroll turns to ash after use
- this is a one-time cast

#### Memorize the Spell
If the spell is not already known, and the caster meets both:
- the class requirement
- the level requirement

then they may memorize the spell instead of casting it from the scroll.

Rules:
- memorization is immediate
- the scroll is destroyed
- the spell is permanently added to that caster's known spell list

### Spellbooks
Spellbooks do **not** exist as physical carried items.

Instead, each caster has access to an internal **spellbook interface** that lists all spells they know.

### Casting Requirements
Umberhold does **not** require a casting focus.

A caster may freely cast any spell they know without needing a focus item or a free hand.

---

## 17. Upcasting and Resting

### Upcasting
Umberhold does **not** use upcasting.

A spell must be cast using a spell slot of its own level only.

### Rule
- a 1st-level spell requires a 1st-level spell slot
- a 2nd-level spell requires a 2nd-level spell slot
- and so on

A lower-level spell may **not** be cast using a higher-level spell slot.

### Resting
The recovery system uses **Resting**.

A Rest takes **8 hours**.

A Rest fully restores:
- all hit points, to maximum
- all spell slots
- any class abilities that are restored by rest, as defined by class rules

### Valid Rest Locations
Resting may only be performed in safe locations, such as:
- inns
- designated safe areas in dungeons

These safe areas should be clearly indicated in the area's description.

### Unsafe Rest Attempt
If the player attempts to rest in an unsafe location, the rest fails with the message:

> **It is not safe to camp here.**

### No Short Rest System
Umberhold does **not** use a short rest mechanic.

---

## 18. Current Approved Spell List Scope

The current approved spell list for:
- cantrips
- 1st-level spells

is maintained in:
- `umberhold/spells-cantrips-1st.md`

This includes the currently approved entries such as:
- Arcbolt
- Beguile
- Blind
- Cure Minor Wounds
- Deathknell of Solace
- Feather Fall
- Identify
- Judgment of Solace
- Litany of Solace
- Mocking Words
- Sleep
- Shockwave
- Shield of Solace
- Solace's Blessing
- Soothe Beast
- Thornburst
- Vaelric's Quietus Key
- Vaelric's Unseen Disarmament
- Venomspit
- Warden's Mark
- Witchlight
- Zarveth's Acid Darts
- Zarveth's Arcane Cloak
- Zarveth's Floating Candle

---

## 19. Conditions

The current approved condition list is:
- Beguiled
- Blinded
- Frightened
- Paralyzed
- Poisoned
- Silenced
- Slept
- Stunned

The detailed rules for these conditions are maintained in:
- `umberhold/conditions-canon.md`

---

## 20. Generic Monster Stat Block

The current approved generic monster stat block is maintained in:
- `umberhold/monster-stat-block-canon.md`

The baseline monster entry currently includes:
- Name
- Description
- Level
- Size
- Type
- Alignment
- AC
- Hit Points
- Strength
- Constitution
- Agility
- Intellect
- Piety
- Personality
- Luck
- Proficiency Bonus
- Saving Throw Proficiencies
- Skill Proficiencies
- Damage Vulnerabilities
- Damage Resistances
- Damage Immunities
- Condition Immunities
- Attacks
- Treasure Type
- Comments
- Experience

### Current Monster Rules Captured by the Generic Stat Block
- monsters use **Level** rather than challenge rating
- current monster levels are **1-20**
- monster sizes are **Small, Medium, Large, Huge, Gigantic**
- Small and Medium occupy **1 slot**
- Large occupies **2 slots**
- Huge occupies **3 slots**
- Gigantic occupies **4 slots**
- unarmored AC starts at **10**
- monster hit dice scale by size: Small **1d6**, Medium **1d8**, Large **1d12**, Huge **2d10**, Gigantic **2d20** per level
- monster proficiency bonus uses the current progression: **1-3 +2, 4-6 +3, 7-9 +4, 10-12 +5, 13-15 +6, 16-18 +7, 19-20 +8**
- monsters use the same seven core attributes as player characters
- monster attributes currently range from **3-30**
- monsters have explicit saving throw proficiencies, skill proficiencies, attacks, and XP value

---

## 21. Experience and Leveling Access

The current approved experience rules are maintained in:
- `umberhold/experience-canon.md`

### Current XP Rules
- monsters award XP based on monster level
- the XP table for monster levels 1-20 is defined
- XP is shared equally among surviving party members
- leveling up is performed at an inn
- leveling up has no gold cost
- full level-up rules will be defined separately

---

## 22. Currency and Gemstones

The current approved currency rules are maintained in:
- `umberhold/currency-canon.md`

The current gemstone reference is maintained in:
- `umberhold/items/gemstones.md`

### Current Currency Rules
- Umberhold uses three coin types: Silver Rook, Gold Crown, and Platinum Stag
- Silver Rook is the base coin
- Gold Crown is worth 10 Silver Rooks
- Platinum Stag is worth 25 Gold Crowns

### Current Gemstone Rules
- gemstones are valid loot-table valuables
- gemstone values are currently tracked in Gold Crowns

---

## 23. Class Hit Dice and Equipment Rules

The current approved class hit-die and equipment rules are maintained in:
- `umberhold/class-equipment-canon.md`

### Current Class Equipment Rules
- each class has a defined hit die per level
- Constitution modifier is added to each hit point roll
- every level requires a hit point roll
- there is no average hit point option
- armor restrictions are absolute
- shield restrictions are absolute
- unusable armor may still be carried but should display in red in inventory
- any class may equip any weapon
- weapon proficiency only affects whether Proficiency Bonus is added to attack rolls
- non-proficient weapon attacks do not gain Proficiency Bonus

---

## 24. Weapon Statistics

The current approved weapon table is maintained in:
- `umberhold/weapon-statistics-canon.md`

### Current Weapon Rules
- weapon entries include damage type
- weapon entries include range values from 1-3
- Quarterstaff is part of the approved weapon table
- finesse weapons may use Strength or Agility, whichever is higher

---

## 25. Approved Rules Currently Locked

The following are currently approved canon:

### Combat Turn Rules
- initiative uses `1d20 + Agility Bonus + modifiers`
- initiative order is shown in a top-left vertical tracker
- active turn holder is highlighted in red
- turn order rotates continuously after each completed turn
- each turn grants one main action
- bonus actions exist, but only when granted by a specific feature or effect
- reactions do not exist
- Defend imposes disadvantage on incoming attacks
- weapon swapping uses the full main action
- Troubadours may use **Sing a Song** as a main action
- extra attacks cannot be redirected if the original target dies

### Damage and Death Rules
- the current list of Umberhold damage types is locked
- vulnerability = double damage
- resistance = half damage, round down, minimum 1 damage
- immunity = no damage
- critical hit on natural 20 by default
- some features may expand critical range
- critical hits roll damage dice twice, then add bonuses
- natural 1 always misses
- death saves are not used
- 0 or fewer hit points means immediate death

### Spellcasting and Recovery Rules
- spellcasting classes start with all class cantrips and all class 1st-level spells
- cantrips do not consume spell slots
- higher-level spells are mainly acquired through adventuring, especially scrolls
- when a caster unlocks a new spell tier, they immediately learn one spell of that level
- scrolls may be cast directly if requirements are met
- scrolls may be memorized if requirements are met and the spell is not already known
- spellbooks are not physical items
- each caster has an internal spellbook interface
- no casting focus is required
- upcasting does not exist
- spells must use slots of their own level only
- Resting takes 8 hours
- Resting fully restores hit points, spell slots, and rest-based class abilities
- Resting only works in safe locations
- unsafe resting fails with a fixed message
- there is no short rest system
- spells explicitly marked as Bonus Action use the bonus action slot for the turn
- the current cantrip and 1st-level spell list is tracked in `umberhold/spells-cantrips-1st.md`

### Condition Rules
- the current approved condition list is Beguiled, Blinded, Frightened, Paralyzed, Poisoned, Silenced, Slept, and Stunned
- detailed condition behavior is tracked in `umberhold/conditions-canon.md`

### Monster Stat Block Rules
- the generic monster stat block is tracked in `umberhold/monster-stat-block-canon.md`
- monsters use Level rather than challenge rating
- current monster levels are 1-20
- monster sizes are Small, Medium, Large, Huge, and Gigantic
- Small and Medium occupy 1 combat slot
- Large occupies 2 combat slots
- Huge occupies 3 combat slots
- Gigantic occupies 4 combat slots
- unarmored monster AC starts at 10
- monster hit dice scale by size: Small 1d6, Medium 1d8, Large 1d12, Huge 2d10, Gigantic 2d20 per level
- monster proficiency bonus uses the current progression: 1-3 +2, 4-6 +3, 7-9 +4, 10-12 +5, 13-15 +6, 16-18 +7, 19-20 +8
- monsters use the same seven core attributes as player characters
- monster attributes currently range from 3-30
- monster entries include Description, damage vulnerabilities, damage resistances, damage immunities, condition immunities, Treasure Type, Comments, attacks, and XP value

### Experience Rules
- the current experience rules are tracked in `umberhold/experience-canon.md`
- monsters award XP based on monster level
- XP is shared equally among surviving party members
- leveling up is performed at an inn
- leveling up has no gold cost

### Currency and Gemstone Rules
- the current currency rules are tracked in `umberhold/currency-canon.md`
- the current gemstone reference is tracked in `umberhold/items/gemstones.md`
- Silver Rook is the base coin
- Gold Crown is worth 10 Silver Rooks
- Platinum Stag is worth 25 Gold Crowns

### Class Equipment Rules
- the current class hit-die and equipment rules are tracked in `umberhold/class-equipment-canon.md`
- each class has a defined hit die per level
- Constitution modifier is added to each hit point roll
- every level requires a hit point roll
- armor restrictions are absolute
- shield restrictions are absolute
- any class may equip any weapon
- non-proficient weapon attacks do not gain Proficiency Bonus

### Weapon Rules
- the current weapon table is tracked in `umberhold/weapon-statistics-canon.md`
- weapon entries include damage type
- weapon entries include range values from 1-3
- Quarterstaff is part of the approved weapon table
- finesse weapons may use Strength or Agility, whichever is higher

---

## 26. Still Open for Later Canonization

The following are still open and should be resolved in future canon passes:

### Combat Open Questions
- initiative tie-break rules
- exact turn timing for status durations
- enemy-side bonus action rules
- whether songs can ever be bonus actions
- whether items can ever be bonus actions
- target invalidation edge cases
- mid-combat initiative changes, if any
- full player formation rules
- full enemy action economy rules

### Damage Open Questions
- interaction order between critical hits and vulnerability/resistance
- whether mixed-damage attacks split damage by type before applying modifiers
- whether damage-over-time effects can critically hit
- whether environmental damage uses the same resistance rules in all cases
- whether Holy / Unholy / Arcane / Shock have special systemic interactions beyond type tags
- whether monsters follow the exact same death rule presentation as player characters

### Spellcasting Open Questions
- exact spell-tier unlock table by class and level
- whether every caster learns the same number of spells when unlocking later tiers beyond the one free spell
- whether scrolls can ever be used by non-casters through special items or class features
- whether rare exceptions can bypass normal class spell lists
- whether some safe dungeon rest locations can be exhausted or used only once
- whether rest can ever be interrupted by scripted events in valid safe zones
- higher-level spell lists beyond 1st level

### Condition Open Questions
- whether Beguiled and Soothed should remain separate conditions or merge into one rules concept
- whether Stunned should prevent all actions instead of only applying attack/save penalties
- whether Frightened affects spell targeting or only attacks
- whether Blinded affects all targeted spell use
- whether bosses have default immunities to specific control conditions
- how cleansing/removal rules are distributed across items, spells, and services
- exact timing for condition expiration when not stated explicitly by a spell or ability

### Monster Open Questions
- whether monster hit points use only size dice or also add Constitution-derived bonuses by level
- whether alignment has any systemic effect beyond lore and spell interaction
- the full canonical skill list used by monsters and characters
- whether monster spellcasters follow player spell slot rules or use bespoke spellcasting packages

### Experience Open Questions
- the exact character XP thresholds required for levels 1-10
- whether benched roster members ever receive shared XP
- whether summoned allies or temporary NPC allies affect XP splitting
- whether story or quest XP exists in addition to monster XP
- whether escape or partial-victory outcomes grant reduced XP
- the exact level-up benefits by class and level

### Currency and Gemstone Open Questions
- whether older `gp` prices in existing notes should be universally converted to Gold Crowns
- whether shops ever display prices directly in mixed denominations
- whether gemstones can have special uses beyond sale value, such as quest, ritual, or crafting functions
- whether gemstones stack in inventory or remain individual items under no-stacking rules

### Class Equipment Open Questions
- whether first-level characters still begin with maximum hit points from their class hit die
- whether off-hand weapon proficiency follows the same rule with no exceptions
- whether class proficiencies can ever be expanded by training, items, or special features
- whether instruments for Troubadours count as weapon-category items for equipment UI purposes
- whether some relic or class effects can temporarily bypass armor restrictions

### Weapon Open Questions
- whether ammunition is abstracted or fully tracked for bows, slings, and crossbows
- whether crossbows have reload-specific handling beyond normal attack use
- whether thrown weapons will exist as a distinct category later
- whether weapon categories should be formalized for class features and item effects
- whether some named weapons gain variant properties beyond the base table

---

## 27. Source Sheets

This consolidated file is currently based on:
- `umberhold/combat-turn-canon.md`
- `umberhold/damage-canon.md`
- `umberhold/spellcasting-canon.md`
- `umberhold/spells-cantrips-1st.md`
- `umberhold/class-spell-lists.md`
- `umberhold/conditions-canon.md`
- `umberhold/monster-stat-block-canon.md`
- `umberhold/experience-canon.md`
- `umberhold/currency-canon.md`
- `umberhold/items/gemstones.md`
- `umberhold/class-equipment-canon.md`
- `umberhold/weapon-statistics-canon.md`

These may still be kept as narrower reference sheets if useful.
