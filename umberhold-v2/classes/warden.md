# Warden

## Class Summary

The **Warden** is a hunter, scout, and wilderness stalker who blends martial skill with divine-nature spellcasting.

### Core Identity
- **Primary Attributes:** Agility / Piety
- **Level 10 Title:** Nature-Wraith
- **Hit Die:** d10
- **Armor:** Light to medium armor
- **Shield:** Can equip shield
- **Weapon Proficiencies:** All single-handed melee weapons, shortbow, longbow, boar spear
- **Spellcasting:** Half caster using **Piety** as the casting attribute

---

## Level Progression

| Level | Title | Feature / Growth Highlights |
|---|---|---|
| 1 | Trail-Hunter | Spellcasting, Ghost of the Wilds, Beast Slayer, Warden's Instinct |
| 2 | Greencloak | Precision |
| 3 | Beast-Stalker | Uncapped Attribute Growth |
| 4 | Thorn-Walker | Dual Wield |
| 5 | Fang-Warden | Extra Attack with shortbow/longbow |
| 6 | Wildrunner | Death Shot |
| 7 | Grey Stalker | Uncapped Attribute Growth |
| 8 | Root-Binder | Favored Enemy |
| 9 | Storm Archer | Concussive Shot |
| 10 | Nature-Wraith | Uncapped Attribute Growth, Multishot |

---

## Features

### Spellcasting
You can cast spells as a **half caster**.

Rules:
- the Warden uses **Piety** as its spellcasting attribute
- spell access and spell recovery follow Umberhold's current spellcasting rules

---

### Ghost of the Wilds
You have advantage on all **Stealth checks outdoors**.

---

### Beast Slayer
You gain:
- **+2 to hit** against beasts
- **+2 damage** against beasts

---

### Warden's Instinct
A Warden's heightened senses reduce the party's chance of being surprised.

Whenever the party would be surprised, if a Warden is present, there is a chance that the party is **not** surprised instead.

### Formula
```text
25% + 1% per point of the Warden's Luck modifier
```

### Multiple Wardens
If multiple Wardens are in the party:
- increase the chance by **10%** for each additional Warden
- use the **highest Luck modifier** among all Wardens when calculating the Luck-based bonus

---

### Precision
Your attacks with a **shortbow** or **longbow** now score a critical hit on a **19-20**.

---

### Uncapped Attribute Growth
You can increase:
- one attribute by **2**
- or two attributes by **1** each

---

### Dual Wield
You can fight with two melee weapons, provided the off-hand weapon is **lighter** than the main-hand weapon.

When you take the **Attack** action with your main-hand weapon, you may make:
- **one additional off-hand attack** as a **bonus action**

---

### Extra Attack
When you attack using a **shortbow** or **longbow**, you may make **two shots at the same target**.

If the target is killed by the first shot, the second shot is **lost**.

---

### Death Shot
Your critical hits have a chance to instantly kill the target.

When you score a critical hit, there is a chance to slay the target outright.

### Formula
```text
5% + 1% per point of your Luck modifier
```

### Restriction
- **Boss-type enemies are immune** to this effect

---

### Favored Enemy
Choose one creature type.

Your attacks against that chosen type deal **one additional damage die**.

### Example
A longbow that normally deals `1d8` instead deals `2d8` against the favored enemy type.

---

### Concussive Shot
Your attacks with a **shortbow** or **longbow** have a chance to **Stun** the target until the end of its next turn.

### Formula
```text
5% + 1% per point of your Luck modifier
```

The effect uses the current **Stunned** condition.

---

### Multishot
When you attack with a **shortbow** or **longbow**:
- fire one attack at your chosen target
- make a second, separate attack against a different target adjacent to it
- roll each attack separately

If there is no adjacent target, you make only **one attack**.

---

## Notes

### Current Role
The Warden is currently defined as:
- ranged striker
- outdoor scout
- beast-hunter
- half caster

### Current Open Mechanical Questions
These may need later clarification:
- how **Extra Attack** and **Multishot** interact at level 10
- whether **Death Shot** and **Concussive Shot** can trigger from every qualifying bow hit in a multi-attack sequence
- whether **Favored Enemy** can ever be changed later or is permanent once chosen
- whether **Warden's Instinct** has a minimum floor if Luck modifier is negative
