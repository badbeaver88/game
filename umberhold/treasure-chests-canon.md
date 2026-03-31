# Umberhold Treasure Chests and Trap Tables

This document captures the current approved working structure for **Treasure Chests** in Umberhold.

It currently defines:
- chest types **A-E**
- lock and trap chances by chest type
- authored trap tables for **Trap Tier A** and **Trap Tier B**

It does **not** modify `MASTER.md`.

---

## 1. General Notes

- chest types are ordered from **A** to **E**
- higher chest types are more likely to be **locked** and **trapped**
- if a chest is trapped, it rolls on a trap tier based on its chest type
- for now, only **Trap Tier A** and **Trap Tier B** are authored here
- entries in each trap table are ordered from **least** to **most lethal** for easier curation
- curses inflicted by chest traps last until dispelled
- when a character is cursed by a chest trap, a **black skull** briefly appears on the player's screen as the status indicator
- if a trap transforms into a monster encounter, the treasure is recovered normally after the creature is defeated

---

## 2. Chest Table

| Type | Container Variants | Locked Chance | Trapped Chance | Trap Tier (if trapped) | Treasure |
|---|---|---|---|---|---|
| **A** | Trunk / Footlocker | **20%** (`DC 5d4`) | **10%** | **85% A, 15% B** | **Chest A** |
| **B** | Strongbox / Iron Coffer | **40%** (`DC 5d4 + 1`) | **25%** | **15% A, 70% B, 15% C** | **Chest B** |
| **C** | Reinforced Chest / Merchant Chest | **60%** (`DC 5d4 + 3`) | **40%** | **15% B, 70% C, 15% D** | **Chest C** |
| **D** | Ornate Chest / Gilded Coffer | **80%** (`DC 5d4 + 5`) | **60%** | **15% C, 70% D, 15% E** | **Chest D** |
| **E** | Jeweled Reliquary / Royal Chest | **95%** (`DC 5d4 + 7`) | **75%** | **15% D, 85% E** | **Chest E** |

---

## 3. Trap Tier A

These are cruel but mostly early-game chest hazards. Unless a trap explicitly says otherwise, **Trap Tier A** saving throws use **DC 10**.

| # | Trap Name | Target | Effect |
|---:|---|---|---|
| 1 | **Curse of Fragile Tools** | Character opening | The target is cursed with **Curse of Fragile Tools**. |
| 2 | **Curse of the Noisy Stomach** | Character opening | The target is cursed with **Curse of the Noisy Stomach**. |
| 3 | **Boneboiler's Greeting** | Character opening | Hot grease sprays from the chest. **Ranged Weapon Attack:** **+2 to hit** against the triggering creature. **Hit:** **2d4 fire** damage, and the target is **Blinded** for **1 minute**. |
| 4 | **Curse of Clumsiness** | Character opening | The target is cursed with **Curse of Clumsiness**. |
| 5 | **Hook in the Velvet** | Character opening | A spring-hook lashes out. **Melee Weapon Attack:** **+3 to hit** against the triggering creature. **Hit:** **1d6 piercing** damage, and the target gains **Bleeding**, taking **1d4 piercing** damage at the start of its next turn. |
| 6 | **Rotwing Nest** | Character opening | A rotwing bursts forth. **Melee Weapon Attack:** **+4 to hit** against the triggering creature. **Hit:** **1d4 + 2 piercing** damage, and the target gains **Bleeding**, taking **1d4 piercing** damage at the start of its next turn. The target must then succeed on a **DC 10 Constitution save** or contract **Veinrot** for **1 hour**. While affected, the target takes **50% more damage** from **Bleeding**. The rotwing flies away after the attack. |
| 7 | **Gloamshadow Seal** | Character opening | A shadowy hand strikes. **Melee Weapon Attack:** **+3 to hit** against the triggering creature. **Hit:** **1d6 cold** damage, and the target's **Strength** score is reduced by **1d2** for **1 hour**. If this reduces the target's **Strength** to **0**, the target dies. |
| 8 | **Curse of Ill Fortune** | Character opening | The target is cursed with **Curse of Ill Fortune**. |
| 9 | **Hungry Lid** | Character opening, then whole party | The chest is a mimic. The triggering creature is targeted by its first attack. **Melee Weapon Attack:** **+5 to hit**. **Hit:** **1d10 + 3 piercing** damage, and the target must succeed on a **DC 13 Constitution save** or become **Paralyzed**. Combat begins. The treasure can be recovered if the mimic is slain. |
| 10 | **Thornburst Hinge** | Whole party | Barbs erupt from the chest. Each creature in range must make a **DC 10 Agility save**, taking **2d4 piercing** damage on a failed save, or half as much on a success. If a creature fails the save by **5 or more**, it also gains **Bleeding**, taking **1d4 piercing** damage at the start of its next turn. |

---

## 4. Trap Tier B

These traps are meant for stronger parties and nastier places. Unless a trap explicitly says otherwise, **Trap Tier B** saving throws use **DC 12**.

| # | Trap Name | Target | Effect |
|---:|---|---|---|
| 1 | **Poppet's Kiss** | Character opening | You hear a child's eerie laugh. **Melee Weapon Attack:** **+5 to hit**. **Hit:** **1 piercing** damage, and the target must make a **DC 12 Constitution save** or take **2d4 poison** damage, or half as much on a success. |
| 2 | **Curse of the Leper** | Character opening | The triggering creature is cursed with **Curse of the Leper**. |
| 3 | **Rotgas** | Whole party | Each creature makes a **DC 12 Constitution save**, taking **1d6 poison** damage on a failed save, or half as much on a success. On a failure, the creature is **Poisoned**. If the save fails by **5 or more**, the creature is also **Blinded** for **1 minute**. |
| 4 | **Curse of Palsy** | Character opening | The triggering creature is cursed with **Curse of Palsy**. |
| 5 | **Translocation** | Whole party | The party is transported to the **dungeon entrance**. **No save.** Chest contents are lost; **quest items** are recovered. |
| 6 | **Curse of Black Wounds** | Character opening | The triggering creature is cursed with **Curse of Black Wounds**. |
| 7 | **Taxman** | Character opening | The triggering creature loses **all coins** it is carrying. |
| 8 | **Rotmother's Belch** | Whole party | Each creature makes a **DC 12 Agility save**, taking **2d6 acid** damage on a failed save, or half as much on a success. |
| 9 | **Stormlash** | Character opening | The triggering creature must make a **DC 12 Agility save** or take **4d6 lightning** damage, or half as much on a success. If the save fails by **5 or more**, the target is also **Paralyzed** for **1 minute**. |
| 10 | **Nullified** | Whole party | All spells affecting creatures and objects in the area are **dispelled**. |
---

## 5. Chest Trap Curse Reference

Curses from these trap tables last until dispelled.

| Curse | Effect |
|---|---|
| **Curse of Ill Fortune** | The cursed character's **Luck** statistic becomes **3**. |
| **Curse of Fragile Tools** | The cursed character's **lockpicks** have a **25% chance to break** whenever they make a **lockpick check**. |
| **Curse of the Leper** | **Healing** done to the cursed character from all sources restores only **50%** of normal. |
| **Curse of Clumsiness** | Whenever the cursed character uses a **magical item with charges**, there is a **25% chance it breaks**. |
| **Curse of the Noisy Stomach** | Whenever the cursed character attempts a **Stealth check**, they emit an obvious noise; such checks are made at **disadvantage**. |
| **Curse of Palsy** | Whenever the cursed character scores a **critical hit**, they instead **fumble their weapon**, dropping it and nullifying the attack. |
| **Curse of Black Wounds** | Any **Bleeding** effect deals **50% more damage** to the cursed character. |

These curses can be ended by any effect that removes curses, including **Remove Curse**.

When a character is cursed by one of these traps, a **black skull** briefly appears on the player's screen as the status indicator.

---

## 6. Authoring Notes

The following trap entries deliberately draw on already-authored Umberhold material, including:
- chest-trap curses and existing **Remove Curse** support
- hostile **Umbraxis** curse flavor for malignant trap effects
- **Thornburst**
- **Boggart Boneboiler** hot grease
- **Boggart Gasser** rotgas
- **Poppet of Pins** poison needle
- **Rotwing** bleeding and **Veinrot**
- **Gloamshadow** Strength-drain touch
- **Chest Mimic**
- **Griselda Rotmother** bile belch
- entries modeled directly on monster attacks now use matching attack-roll profiles where appropriate

---

## 7. Still To Be Authored Later

- **Trap Tier C**
- **Trap Tier D**
- **Trap Tier E**
- **Treasure Table A**
- **Treasure Table B**
- later treasure tables beyond **B**

---

## 8. Implementation Note

This file is a standalone chest-and-trap reference sheet.
It does **not** modify `MASTER.md`.
