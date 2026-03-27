# Umberhold Combat Turn Canon

This document captures the current approved rules for **initiative, turn order, and combat actions**.

It is written as an Umberhold-native rules reference and avoids external system branding.

---

## 1. Combat Start

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

## 8. Combat Interface Implications

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

## 9. Approved Rules Captured Here

This document locks in the following:
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

---

## 10. Still Open for Later Canonization

The following are not finalized in this document and should be resolved in broader combat canon:
- initiative tie-break rules
- exact turn timing for status durations
- enemy-side bonus action rules
- whether songs can ever be bonus actions
- whether some spells or items can be bonus actions
- target invalidation edge cases
- mid-combat initiative changes, if any
- full player formation rules
- full enemy action economy rules

---

## 11. Implementation Note

This file does **not** modify any master reference document.
It exists as a standalone approved combat-turn rules sheet.
