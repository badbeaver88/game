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

These are cruel but mostly early-game chest hazards. They are meant to wound, panic, separate, or punish greed without making every trap an automatic death sentence.

| # | Trap Name | Target | Effect |
|---:|---|---|---|
| 1 | **Curse of Fragile Tools** | Character opening | A black locksmith's sigil flashes across the opener's hands. **DC 10 Piety save** or be cursed with **Curse of Fragile Tools**. |
| 2 | **Curse of the Noisy Stomach** | Character opening | A sour green rune sinks into the gut and answers stealth with humiliating noise. **DC 10 Piety save** or be cursed with **Curse of the Noisy Stomach**. |
| 3 | **Boneboiler's Greeting** | Character opening | A hidden bladder of hot grease bursts across the face and hands. **+2 to hit** against the character opening. On a hit, the target takes **2d4 fire** damage and becomes **Blinded** until the **end of its next turn**. |
| 4 | **Curse of Clumsiness** | Character opening | A greasy charm brands the fingertips and turns charged magic fickle. **DC 11 Piety save** or be cursed with **Curse of Clumsiness**. |
| 5 | **Hook in the Velvet** | Character opening | A spring-hook punches through the wrist and tears free. **+3 to hit** against the character opening. On a hit, the target takes **1d6 piercing** damage and gains **Bleeding**, taking **1d4 piercing** damage at the start of its next turn. |
| 6 | **Thornburst Hinge** | Whole party | Blackened barbs and root-thorns explode outward from the chest seams. Each party member must make a **DC 11 Agility save** or take **2d4 piercing** damage. If the save fails by **5 or more**, that character also gains **Bleeding** for **1d4 piercing** damage at the start of their next turn. On a success, take half damage. |
| 7 | **Rotwing Nest** | Character opening | A starving rotwing bursts from a false coin layer and makes a **Proboscis** attack: **+4 to hit** against the character opening. On a hit, the target takes **1d4 + 2 piercing** damage and gains **Bleeding**, taking **1d4 piercing** damage at the start of its next turn. If the hit lands, the target must then make a **DC 10 Constitution save** or contract **Veinrot** for **1 hour**. While affected by **Veinrot**, the target takes **50% more damage** from **Bleeding** effects. |
| 8 | **Gloamshadow Seal** | Character opening | A hand of cold dusk closes over the heart. **+3 to hit** against the character opening. On a hit, the target takes **1d6 cold** damage and loses **1d2 Strength** for **1 hour**. If this reduces the target's **Strength to 0**, the target dies. |
| 9 | **Curse of Ill Fortune** | Character opening | A dead coin stamped with Umbraxis' grin spins once and vanishes. **DC 11 Piety save** or be cursed with **Curse of Ill Fortune**. |
| 10 | **Hungry Lid** | Character opening, then whole party | The chest splits along wet seams and becomes a **Chest Mimic**. The opener is immediately targeted by its first bite: **+5 to hit**, **1d10 + 3 piercing** damage, and the target must make a **DC 13 Constitution save** or become **Paralyzed**. After that strike, combat begins. The treasure is recovered if the mimic is slain. |

---

## 4. Trap Tier B

These traps are meant for stronger parties and nastier places. They lean harder into burst damage, permanent pressure, and effects that can turn a successful expedition into a crawl back to safety.

| # | Trap Name | Target | Effect |
|---:|---|---|---|
| 1 | **Poppet's Kiss** | Character opening | A spring-loaded needle jabs with doll-like precision. **+5 to hit** against the character opening. On a hit, the target takes **1 piercing** damage, then must make a **DC 12 Constitution save** or take **2d4 poison** damage. On a success, the poison damage is halved. |
| 2 | **Curse of the Leper** | Character opening | A chalk-white handprint blooms across the skin. **DC 12 Piety save** or be cursed with **Curse of the Leper**. |
| 3 | **Rotgas Reliquary** | Whole party | A buried censer cracks open and floods the space with embalmed poison fog. Each party member must make a **DC 11 Constitution save** or take **1d6 poison** damage and become **Poisoned**. If the save fails by **5 or more**, that character is also **Blinded** for **1 minute**. On a success, take half damage and avoid the conditions. |
| 4 | **Curse of Palsy** | Character opening | Dead nerves writhe beneath the hand and weapon-arm. **DC 12 Piety save** or be cursed with **Curse of Palsy**. |
| 5 | **The Long Walk Home** | Whole party | The chest gives a single, hateful click. The floor, walls, and air fold like rotten cloth, and the party is hurled back to the **entrance or start** of the current dungeon. **No save.** All **non-magical light sources** currently burning are extinguished. |
| 6 | **Curse of Black Wounds** | Character opening | A black seam opens across old scars and fresh cuts alike. **DC 13 Piety save** or be cursed with **Curse of Black Wounds**. |
| 7 | **Gloamshadow Hand** | Character opening | A black, freezing grasp reaches out from inside the coffer and makes a **Weakening Touch** attack: **+3 to hit** against the character opening. On a hit, the target takes **1d6 cold** damage and loses **1d3 Strength** for **1 hour**. If this reduces the target's **Strength to 0**, the target dies. |
| 8 | **Rotmother's Belch Jar** | Whole party | A sealed crock of bile, grease, and half-digested filth detonates across the party. Each party member must make a **DC 12 Agility save** or take **2d6 acid** damage. On a success, take half damage. |
| 9 | **Thorn-Coffin Mechanism** | Whole party | The chest blossoms into a cage of iron roots and inward-pointing thorns. Each party member must make a **DC 12 Agility save** or take **2d4 + 2 piercing** damage. If the save fails by **5 or more**, that character also gains **Bleeding** for **1d4 piercing** damage at the start of their next turn. On a success, take half damage. |
| 10 | **Umbraxis' Black Benediction** | Whole party | The chest erupts in a devouring flare of black-violet radiance. Each party member must make a **DC 13 Piety save** or take **3d8 unholy** damage and become **Blinded** for **1 minute**. On a success, take half damage and avoid the blindness. |

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

---

## 6. Authoring Notes

The following trap entries deliberately draw on already-authored Umberhold material, including:
- chest-trap curses and existing **Remove Curse** support
- **Umbraxis** curse and judgment motifs
- **Thornburst**
- **Boggart Boneboiler** **Meat Hook** and **Hurl Hot Grease**
- **Boggart Gasser** rotgas
- **Poppet of Pins** poison needle
- **Rotwing** bleeding and **Veinrot**
- **Gloamshadow** **Weakening Touch**
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
