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
| 1 | **Ashen Sneeze-Wire** | Character opening | A puff of grave-dust bursts into the eyes and lungs. **DC 10 Constitution save** or take **1d4 poison** damage and become **Blinded** for **1 minute**. On a success, take half damage and avoid the condition. |
| 2 | **Taxman in the Lock** | Whole party | A gaunt, smiling revenant tallies the party's wealth with a bone stylus, then takes its due. **No save.** The party loses **10% of its carried gold**, rounded up. The chest may still be opened afterward if no other hazard remains. |
| 3 | **Bell-Wire of Umbraxis** | Character opening | A tiny black funeral bell tolls inside the skull. **DC 10 Piety save** or take **1d4 psychic** damage. If the save fails by **5 or more**, the target is also **Frightened** for **1 minute**. |
| 4 | **Boneboiler's Greeting** | Character opening | A hidden bladder of hot grease bursts across the face and hands. **DC 10 Agility save** or take **2d4 fire** damage and become **Blinded** for **1 minute**. On a success, take half damage and avoid the blindness. |
| 5 | **Rotgas Latch** | Whole party | The lid exhales a sealed cloud of corpse-green boggart gas. Each party member must make a **DC 10 Constitution save** or take **1d4 poison** damage and become **Poisoned**. If a save fails by **5 or more**, that character is also **Blinded** for **1 minute**. On a success, take half damage and avoid both conditions. |
| 6 | **Hook in the Velvet** | Character opening | A spring-hook punches through the wrist and tears free. **DC 11 Agility save** or take **1d6 piercing** damage and gain **Bleeding** for **1d4 piercing** damage at the start of the target's next turn. On a success, take half damage and avoid **Bleeding**. |
| 7 | **Thornburst Hinge** | Whole party | Blackened barbs and root-thorns explode outward from the chest seams. Each party member must make a **DC 11 Agility save** or take **2d4 piercing** damage. If the save fails by **5 or more**, that character also gains **Bleeding** for **1d4 piercing** damage at the start of their next turn. On a success, take half damage. |
| 8 | **Rotwing Nest** | Character opening | A starving rotwing bursts from a false coin layer and drives its proboscis deep. **DC 10 Agility save** or take **1d4 + 2 piercing** damage and gain **Bleeding** for **1d4 piercing** damage at the start of the target's next turn. If the hit lands, the target must then make a **DC 10 Constitution save** or contract **Veinrot** for **1 hour**. While affected by **Veinrot**, the target takes **50% more damage** from **Bleeding** effects. |
| 9 | **Gloamshadow Seal** | Character opening | A hand of cold dusk closes over the heart. **DC 11 Piety save** or take **1d6 cold** damage and lose **1d2 Strength** for **1 hour**. If this reduces the target's **Strength to 0**, the target dies. On a success, take half damage and avoid the Strength loss. |
| 10 | **Hungry Lid** | Character opening, then whole party | The chest splits along wet seams and becomes a **Chest Mimic**. The opener is immediately targeted by its first bite: **+5 to hit**, **1d10 + 3 piercing** damage, and the target must make a **DC 13 Constitution save** or become **Paralyzed**. After that strike, combat begins. The treasure is recovered if the mimic is slain. |

---

## 4. Trap Tier B

These traps are meant for stronger parties and nastier places. They lean harder into burst damage, permanent pressure, and effects that can turn a successful expedition into a crawl back to safety.

| # | Trap Name | Target | Effect |
|---:|---|---|---|
| 1 | **Venomspit Ampoule** | Character opening | A glass ampoule snaps under the latch and spits corrosive venom upward. **DC 11 Agility save** or take **2d4 acid** damage. On a success, take half damage. |
| 2 | **Poppet's Kiss** | Character opening | A spring-loaded needle punches into the flesh with doll-like precision. The target takes **1 piercing** damage, then must make a **DC 12 Constitution save** or take **2d4 poison** damage. On a success, the poison damage is halved. |
| 3 | **Rotgas Reliquary** | Whole party | A buried censer cracks open and floods the space with embalmed poison fog. Each party member must make a **DC 11 Constitution save** or take **1d6 poison** damage and become **Poisoned**. If the save fails by **5 or more**, that character is also **Blinded** for **1 minute**. On a success, take half damage and avoid the conditions. |
| 4 | **Arcbolt Cage** | Character opening | Copper wire and damp iron teeth snap shut in a crackling halo. **DC 12 Agility save** or take **3d4 lightning** damage. On a success, take half damage. |
| 5 | **The Long Walk Home** | Whole party | The chest gives a single, hateful click. The floor, walls, and air fold like rotten cloth, and the party is hurled back to the **entrance or start** of the current dungeon. **No save.** All **non-magical light sources** currently burning are extinguished. |
| 6 | **Grave Slurry Reservoir** | Character opening | A hidden sac of corpse-sludge bursts over the arms and gear. **DC 12 Agility save** or take **2d4 acid** damage and suffer a **MINOR ITEM DESTRUCTION** check with **DC 5**. On a success, take half damage and avoid the item check. |
| 7 | **Gloamshadow Hand** | Character opening | A black, freezing grasp reaches out from inside the coffer and drinks the target's strength. **DC 12 Piety save** or take **1d6 cold** damage and lose **1d3 Strength** for **1 hour**. If this reduces the target's **Strength to 0**, the target dies. On a success, take half damage and avoid the Strength loss. |
| 8 | **Rotmother's Belch Jar** | Whole party | A sealed crock of bile, grease, and half-digested filth detonates across the party. Each party member must make a **DC 12 Agility save** or take **2d6 acid** damage. On a success, take half damage. |
| 9 | **Thorn-Coffin Mechanism** | Whole party | The chest blossoms into a cage of iron roots and inward-pointing thorns. Each party member must make a **DC 12 Agility save** or take **2d4 + 2 piercing** damage. If the save fails by **5 or more**, that character also gains **Bleeding** for **1d4 piercing** damage at the start of their next turn. On a success, take half damage. |
| 10 | **Umbraxis' Black Benediction** | Whole party | The chest erupts in a devouring flare of black-violet radiance. Each party member must make a **DC 13 Piety save** or take **3d8 unholy** damage and become **Blinded** for **1 minute**. On a success, take half damage and avoid the blindness. |

---

## 5. Authoring Notes

The following trap entries deliberately draw on already-authored Umberhold material, including:
- existing divine bell-curse effects
- **Arcbolt**
- **Thornburst**
- existing divine judgment effects, re-skinned here for **Umbraxis**
- **Boggart Gasser** rotgas
- **Boggart Boneboiler** hot grease
- **Poppet of Pins** poison needle
- **Rotwing** bleeding and **Veinrot**
- **Gloamshadow** Strength-drain touch
- **Chest Mimic**
- **Grave Slurry** acid and item corrosion
- **Griselda Rotmother** bile belch

---

## 6. Still To Be Authored Later

- **Trap Tier C**
- **Trap Tier D**
- **Trap Tier E**
- **Treasure Table A**
- **Treasure Table B**
- later treasure tables beyond **B**

---

## 7. Implementation Note

This file is a standalone chest-and-trap reference sheet.
It does **not** modify `MASTER.md`.
