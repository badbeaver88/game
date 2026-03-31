# Umberhold Lesser Magical Items

This document captures the current approved **Lesser** magical item list for Umberhold.

Magical items are grouped into three tiers:
- **Lesser**
- **Greater**
- **Exalted**

This file currently covers the **Lesser** tier only.

It does **not** modify `DESIGN.md`.

---

## General Notes

- weights use **stones**
- values are shown in **Gold Crowns**
- entries marked **Varies** inherit the underlying weapon or armor weight
- entries marked **Random** require item-generation tables that are not yet authored here

---

## Lesser Magical Item Table

| Item Name | Type | Weight | Value | Effect |
|---|---|---:|---|---|
| **Potion of Healing** | Potion | 1 stone | 50 Gold Crowns | Heals **3d6 + 3 hit points** when consumed. |
| **Potion of Cleansing** | Potion | 1 stone | 100 Gold Crowns | Removes **all poisons and diseases** when consumed. |
| **Scroll of Random 1st-Level Spell** | Scroll | 1 stone | 75 Gold Crowns | Contains one **random 1st-level spell**. |
| **Scroll of Random 2nd-Level Spell** | Scroll | 1 stone | 150 Gold Crowns | Contains one **random 2nd-level spell**. |
| **Random +1 Weapon** | Weapon | Varies | 500 Gold Crowns | Grants **+1 to attack and damage rolls**. Weapon type is determined randomly. |
| **Random +1 Light Armor** | Armor (Body) | Varies | 400 Gold Crowns | Grants **+1 AC**. Light armor type is determined randomly. |
| **Random +1 Medium Armor** | Armor (Body) | Varies | 600 Gold Crowns | Grants **+1 AC**. Medium armor type is determined randomly. |
| **+1 Shield** | Shield (Off-hand) | 6 stones | 500 Gold Crowns | Grants **+1 AC**. |
| **Potion of Dragon's Breath** | Potion | 1 stone | 150 Gold Crowns | Breathe on one enemy at **range 1**. The breath hits the target and any adjacent enemies on either side, dealing **3d8 elemental damage**. **DC 15 Agility save** for half damage. Comes in four variants: **Red** (fire), **Black** (acid), **Blue** (lightning), and **White** (cold). |
| **Potion of Marrow Muncher Strength** | Potion | 1 stone | 200 Gold Crowns | Strength becomes **18 for 1 hour**. A Marrow Muncher is a hairy, ogre-like creature. |
| **Gloves of the Black Hand** | Gloves (Hands) | 1 stone | 250 Gold Crowns | Grants **+4 to Lockpicking and Remove Traps checks**. |
| **Gauntlets of the Marrow Muncher** | Gloves (Hands) | 2 stones | 600 Gold Crowns | Grants **Strength 18** while worn. |
| **Mithral Chain Shirt** | Armor (Body) | 5 stones | 800 Gold Crowns | Functions as a chain shirt; weight is reduced to **5 stones** and it imposes **no Agility modifier penalty**. |
| **Zarveth's Shifting Cloak** | Cloak (Back) | 1 stone | 700 Gold Crowns | A purple-blue patchwork cloak that shifts in the light. Grants **+2 AC**. Does **not** stack with similar spell effects. **Cannot be worn over armor**. |
| **Sunblade** | Weapon (Any Sword) | Varies | 600 Gold Crowns | The weapon is any sword, determined randomly. When equipped, it provides **magical illumination (3 squares)**. |
| **Ring of Feather Falling** | Ring (Finger) | no weight | 400 Gold Crowns | The wearer is **immune to falling damage**. |
| **Graveveil Cloak** | Cloak (Back) | 1 stone | 500 Gold Crowns | Made of shifting leather skinned from graveyard bodies. While worn, there is a **5% chance + Luck modifier** that damage which would reduce the wearer to **0 hit points** instead leaves them at **1 hit point**. When found, it has **2d4 + 2 charges**. |
| **Potion of Speed** | Potion | 1 stone | 250 Gold Crowns | Lasts **1 hour** and grants **advantage on Initiative rolls**. |
| **Woodland Bracers** | Gloves (Hands) | 1 stone | 350 Gold Crowns | Leather bracers tooled from woodland creatures. Grants **+2 to attack rolls with shortbow and longbow**. |
| **Cap of the Unbound Mind** | Cap (Head) | 1 stone | 300 Gold Crowns | The wearer has **advantage against spells and effects that would Beguile** them. |
| **Bonepick Key** | Key | no weight | 100 Gold Crowns | Carved from a thief's finger bone. Opens **one lock**, then crumbles to dust. |
| **Zarveth's Wand** | Wand (Held) | 1 stone | 650 Gold Crowns | A dark, root-like wand of twisted wood. When found, it has **4d10 charges**. **Hedge Wizard only.** It casts **Zarveth's Acid Darts**: target one enemy; make **three ranged spell attacks** (**d20 + Proficiency Bonus + Casting Bonus vs AC**). Each hit deals **1d4 + 1 poison** damage. If any attack is a natural 20, the target is **Poisoned** until the end of its next turn. |
| **Gravebreaker Mace** | Weapon (Mace) | 4 stones | 550 Gold Crowns | Deals an extra **2d6 holy damage** to undead. |
| **Shadowman's Blade** | Weapon (Katana) | 3 stones | 650 Gold Crowns | Grants **+1 to attack and damage rolls**. **Only when wielded by a Shadowman**, its hits cause **Bleeding**, dealing an extra damage die at the start of the target's next turn. |

---

## Implementation Notes

- **Scroll of Random 1st-Level Spell** and **Scroll of Random 2nd-Level Spell** still need their random spell tables.
- **Random +1 Weapon**, **Random +1 Light Armor**, **Random +1 Medium Armor**, **Sunblade**, and similar entries still need their subtype roll tables.
- **Graveveil Cloak** has a defined starting charge count, but the exact charge-consumption rule should be confirmed during implementation.
- **Zarveth's Wand** uses the already approved **Zarveth's Acid Darts** spell profile.

---

## Status

This file establishes the first authored tier of Umberhold magical items.
**Greater** and **Exalted** magical item lists still need to be created.
