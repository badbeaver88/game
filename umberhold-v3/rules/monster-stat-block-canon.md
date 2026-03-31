# Umberhold Monster Stat Block Canon

This document captures the current approved generic monster stat block for Umberhold.

It defines the baseline fields used to build monster entries.

It does **not** modify `DESIGN.md`.

---

## 1. Core Monster Fields

| Field | Details |
|---|---|
| Name | Name of the creature |
| Description | Describes the creature in detail, including appearance, odor, demeanor, behavior, and other sensory notes |
| Level | 1-20 |
| Size | Small, Medium, Large, Huge, or Gigantic |
| Type | Beast, Construct, Dragon, Elemental, Fey, Fiend, Giant, Humanoid, Insect, Monstrosity, Ooze, Plant, or Undead |
| Alignment | Good, Neutral, or Evil |
| AC | Base 10 when unarmored, modified by Agility, armor, and other effects |
| Hit Points | Determined by size and level |
| Strength | 3-30 |
| Constitution | 3-30 |
| Agility | 3-30 |
| Intellect | 3-30 |
| Piety | 3-30 |
| Personality | 3-30 |
| Luck | 3-30 |
| Proficiency Bonus | Based on level progression |
| Saving Throw Proficiencies | List of proficient saves |
| Skill Proficiencies | List of proficient skills |
| Damage Vulnerabilities | List of damage vulnerabilities |
| Damage Resistances | List of damage resistances |
| Damage Immunities | List of damage immunities |
| Condition Immunities | List of condition immunities |
| Attacks | List of attacks, including to-hit, damage, damage type, and special effects |
| Traits | Optional passive, reactive, or always-on monster abilities, usually presented in a separate trait section or table |
| Treasure Type | Treasure category from A-Z, based on treasure tables |
| Comments | Optional creature comments, including a 5% chance at the start of its turn to speak a random humorous line appropriate to its creature type |
| Experience | XP awarded to the party for slaying the monster |

---

## 2. Monster Level

Monsters use a **Level** value rather than an external challenge rating style label.

Current monster level range:
- **1-20**

---

## 3. Monster Size

Monster size categories are:
- Small
- Medium
- Large
- Huge
- Gigantic

### Combat Occupancy Mapping
Under Umberhold's current combat system, size maps to enemy rank occupancy as follows:
- Small = 1 slot
- Medium = 1 slot
- Large = 2 slots
- Huge = 3 slots
- Gigantic = 4 slots

---

## 4. Monster Types

The current approved monster types are:
- Beast
- Construct
- Dragon
- Elemental
- Fey
- Fiend
- Giant
- Humanoid
- Insect
- Monstrosity
- Ooze
- Plant
- Undead

---

## 5. Alignment

The current approved alignment values are:
- Good
- Neutral
- Evil

---

## 6. Armor Class

Monster AC uses a base of **10** when unarmored.

AC may then be modified by:
- armor
- Agility bonus
- magical effects
- other special modifiers

---

## 7. Hit Point Progression by Size

Monster hit points are based on size.

| Size | Hit Dice per Level |
|---|---|
| Small | 1d6 per level |
| Medium | 1d8 per level |
| Large | 1d12 per level |
| Huge | 2d10 per level |
| Gigantic | 2d20 per level |

---

## 8. Core Attributes

All monsters use the same seven core attributes as player characters:
- Strength
- Constitution
- Agility
- Intellect
- Piety
- Personality
- Luck

Each attribute currently ranges from:
- **3-30**

---

## 9. Proficiency Bonus by Level

| Level Range | Proficiency Bonus |
|---|---|
| 1-3 | +2 |
| 4-6 | +3 |
| 7-9 | +4 |
| 10-12 | +5 |
| 13-15 | +6 |
| 16-18 | +7 |
| 19-20 | +8 |

---

## 10. Saving Throw and Skill Proficiencies

Monsters may have:
- saving throw proficiencies
- skill proficiencies

If a monster is proficient in a save or skill, it adds its proficiency bonus to the relevant roll.

---

## 11. Damage and Condition Defenses

Monster entries may include:
- damage vulnerabilities
- damage resistances
- damage immunities
- condition immunities

These should use Umberhold's current damage types and condition list.

---

## 12. Attacks

A monster's attack list should include, at minimum:
- attack name
- to-hit bonus
- damage
- damage type
- range
- any attached effects or conditions

### Attack Range Rule
Every monster attack must have a **range value from 1-3**.

---

## 13. Traits, Treasure, Comments, and Experience

### Traits
Each monster may include a **Traits** section.

This is used for passive, reactive, or always-on abilities such as:
- regeneration
- aura effects
- triggered behaviors
- special weaknesses or compulsions

### Treasure Type
Each monster may include a **Treasure Type** field from **A-Z**, based on Umberhold's treasure tables.

### Comments
Each monster may include a **Comments** field.

This currently supports flavor such as:
- a **5% chance** at the start of its turn to speak a random humorous line appropriate to its creature type

### Experience
Each monster should include an **Experience** value showing how much XP is awarded to the party for slaying it.

The exact XP values by monster level are maintained in:
- `rules/experience-canon.md`

---

## 14. Approved Rules Captured Here

This document locks in the following:
- monsters use Level rather than challenge rating
- current monster levels are 1-20
- monsters use the five size categories Small, Medium, Large, Huge, and Gigantic
- Small and Medium occupy 1 combat slot
- Large occupies 2 combat slots
- Huge occupies 3 combat slots
- Gigantic occupies 4 combat slots
- the current monster type list is Beast, Construct, Dragon, Elemental, Fey, Fiend, Giant, Humanoid, Insect, Monstrosity, Ooze, Plant, and Undead
- the current alignment values are Good, Neutral, and Evil
- unarmored AC starts at 10
- hit point dice scale by size category
- monsters use the same seven core attributes as player characters
- monster attributes currently range from 3-30
- proficiency bonus follows the current level progression table
- monster entries include a Description field
- monster entries include saving throw proficiencies and skill proficiencies
- monster entries may include damage vulnerabilities, damage resistances, damage immunities, and condition immunities
- monster entries may include a Traits section for passive, reactive, or always-on abilities
- monster entries include attacks and XP value
- monster entries may include Treasure Type and Comments

---

## 15. Still Open for Later Canonization

The following are still open and may need later clarification:
- whether monster hit points use only size dice or also add Constitution-derived bonuses by level
- whether alignment has any systemic effect beyond lore and spell interaction
- the full canonical skill list used by monsters and characters
- whether monster spellcasters follow player spell slot rules or use bespoke spellcasting packages

---

## 16. Implementation Note

This file is a standalone approved rules sheet.
It does **not** modify `DESIGN.md`.
