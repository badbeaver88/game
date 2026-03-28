



{{insideCover}}

# Umberhold

___

{{imageMaskCenter5,--offsetX:0%,--offsetY:0%,--rotation:0
  ![background image](https://i.imgur.com/IsfUnFR.jpg){position:absolute,bottom:0,left:0,height:100%}
}}








\page





# System Prompt: Umberhold Engine Architect

**Role:** You are a Lead Game Developer and Systems Architect. Your task is to build the foundational logic for "Umberhold," a 1st-person dungeon crawler merging *The Bard’s Tale* exploration with *Wizardry: Daphne* tactical combat.

## 1. Spatial Constraints (The $26 \times 26$ Grid)
Implement a coordinate-based map system.
* **Format:** $A1$ through $Z26$.
* **Logic:** Each coordinate must support a `Tile` object containing:
    * `is_wall`: Boolean
    * `texture_id`: Reference for 1st-person rendering.
    * `on_step_trigger`: Reference to a narrative event or a "Set Piece" encounter.
* **Encounters:** Separate `RandomTable` (probability-based) from `FixedEncounter` (coordinate-triggered story beats).

## 2. Tactical Rank & Slot System (The "6-Slot" Rule)
Combat occurs on a 4-rank linear axis: `[Party Rear] [Party Front] | [Enemy Front] [Enemy Rear]`.
* **The 6-Slot Constraint:** Each Enemy Rank has a capacity of **6 slots**.
* **Entity Sizing:** * `Medium`: 1 slot | `Large`: 2 slots | `Huge`: 3 slots | `Gigantic`: 4 slots.
* **The "Advance" Algorithm:** On `turn_end`, if `Enemy_Front` has available slots, `Enemy_Rear` entities with the `Melee` tag must move forward to fill the gap if their size allows.

## 3. Combat Calculus (Range 1-3)
All actions (Melee, Ranged, Spells) must validate via the `RangeCheck` function:
* **Distance Constants:** * Adjacent Ranks = Distance 1.
    * One Rank Gap = Distance 2.
    * Two Rank Gap = Distance 3.
* **Constraint:** If `Weapon_Range < Distance`, the action is invalid.

## 4. 5E Custom Race Engine
Characters are 5th Edition D&D based with some custom features. Characters start at 1st level and can advance to 10th level, which is the current maximum. 
* **Modular Race Class:** Create a class that allows for negative modifiers and custom base AC.
* **Example Case (Hillkin):** * `Ability_Mods`: {STR: +1, CON: +1}
    * `Base_AC`: 11 (replaces standard 10).
    * `Save_Penalty`: {DEX_SAVE: -4}.

## 5. Implementation Requirements
1. **State Machine:** Define `STATE_EXPLORE`, `STATE_COMBAT`, and `STATE_DIALOGUE`.
2. **Data Structure:** Provide a JSON template for a `Monster` that includes its `slot_size`, `primary_range`, and `5E_stats`.
3. **Narrative Flag System:** A global dictionary to track story progress so "Set Pieces" change based on previous player choices.



\page

##### The Plot



### **The Cold Horizon**
In the far northern reaches of **Chillandrial**, the golden spires of **Valashu**—the holy jewel of the realm—have gone dark. The **Lord Patriarch**, the living voice of the **Solcine Church**, has vanished. From the **Necropolis of Malakor**, an ancient Lich King has clawed his way back into the world, turning the capital into a city of the silent dead.

But to the people of **Umberhold**, a muddy village on the southern outskirts of the world, Valashu is a fairy tale. Here, the struggle is not for the soul of the world, but for the next meal.

### **The Lowly Beginnings**
You are not knights, paladins, or scholars. You are the **Bone Pickers**, scavenging the scraps of the old world; the **Dung Collectors**, tilling the waste of the new; and the **Chimney Sweeps**, breathing the soot of a dying age. You live in the shadow of the aristocracy’s neglect, ignored by the wars of the north.

### **The Shadows of Gravenhollow**
The darkness has finally come for the forgotten. On the edge of the village sits **Gravenhollow Manor**, a sprawling, derelict estate that has remained locked for generations. Now, the gates have groaned open. People are disappearing from their beds. Strange, rhythmic chanting echoes through the village at night, and the local graveyards are stirring.

### **The Descent and the Ascent**
Your journey begins with a simple, desperate task: enter **Gravenhollow Manor** to find the missing villagers. But what starts as a search for neighbors reveals a terrifying truth—the Manor is a conduit, a southern anchor for the Lich King’s power. 

As you fight through the manor's $26 \times 26$ grid of horrors, you will realize that the "Bone Picking" you’ve done your whole life was training for this. You must gather the scattered relics of the **Solcine Church**, survive the tactical onslaught of the Lich’s ranks, and march North. 

From the soot-stained streets of Umberhold to the blood-soaked altars of the **Necropolis of Malakor**, you will rise. Not because you were chosen by destiny, but because you were the only ones left to pick up the sword.





\page




# **PROJECT: UMBERHOLD**

**Core Concept:** A dark, narrative-driven RPG where a party of six characters must survive a series of $26 \times 26$ grids to defeat a Lich King in the frozen North. A classic rpg/dungeon crawler in the theme of the Bard's Tale Trilogy and Wizardry Daphne.

---

## **I. World & Regional Architecture**
The world is a collection of interconnected **Regional Grids**.
* **The Grid:** Every area (City, Dungeon, Wilderness) is a strictly defined **$26 \times 26$ coordinate map** ($A1$ to $Z26$).
* **Perspective:** 1st-person, grid-based "step" movement (Bard's Tale style). The player's point od view turns 90 degrees per turn.
* **Climates:** * **The Muddy South (Umberhold):** Starting region. Dark, damp, and soot-stained.
    * **The Frozen North (Valashu):** Tundra and ice leading to the capital city.
    * **Hazardous Zones:** Volcanic rifts and blighted wastes with unique environmental status effects.
* **Transition Logic:** Moving between regions occurs at specific "Transit Coordinates" at the edge of a grid.

---

## **II. Combat: The Tactical Rank Engine**
Combat transitions to a stationary, tactical view with a **4-rank axis**.
* **Formation:** `[Party Rear] [Party Front] | [Enemy Front] [Enemy Rear]`.
* **The 6-Slot Rule:** Each enemy rank contains **6 horizontal slots**.
    * **Small/Medium:** 1 Slot | **Large:** 2 | **Huge:** 3 | **Gigantic:** 4.
* **Range Mechanics (Scale 1–3):**
    * **Range 1:** Hits adjacent rank only.
    * **Range 2:** Hits across one rank (e.g., Party Rear ↔ Enemy Front).
    * **Range 3:** Hits the furthest rank (e.g., Party Rear ↔ Enemy Rear).
* **AI Movement:** Melee monsters automatically "Advance" to fill empty front-rank slots as a free action on their turn. Also, some monsters who favor ranged attacks (spells and bows, for example), will prefer to remain in the rear and not advance.

---

## **III. Character & Custom Systems**
* **The Party:** 6 player-created characters.
* **Progression:** Levels 1 to 10 (Current Max). 
* **Custom Races:** Modular ancestry with heavy trade-offs.
    * **Hillkin:** +1 STR, +1 CON, 11 Base AC, and a **-4 penalty to Agility (DEX) saves**.
* **Stat Core:** Uses Strength, Agility (equivilent of Dexterity in 5E), Constitution, Intellect (equivilent of Intelligence in 5E), Piety (equivilent of Wisdom in 5E), Personality (equivilent of Charisma in 5E) and Luck (a new statistic not present in 5E).
* **Inventory:** Weight-based and slot-based system (paperdoll) for weapons/items adapted for the 1–3 Range system.

---

## **IV. The Village Hub: Umberhold**
The starting village functions as a "Town Menu" for management and narrative progression.

| Location | NPC | Primary Services |
| :--- | :--- | :--- |
| **Umberhold Inn** | **Bartholomew** | **Long Rest**, Create/Delete/Swap characters. |
| **Iron Shovel & Scutage** | **Oswaldine** | Buy/Sell gear; Identify items at a cost. |
| **Solcine Chantry** | **Acolyte Gidney** | Healing; Resurrection ($500gp \times Level$). |
| **The Bailiff’s Desk** | **Wymarc** | Narrative side-quests. |
| **Alchemist’s Mortar** | **Etheldreda** | Primarily **Potions** but other minor magical items. |

> **The Hollow Risk:** Resurrection has a **failure rate**, 20% base, reduced by **1% for every point of the character's Constitution** score.



\page


What is the player doing most of the time? 


---
### **Player Activity Summary**

In **Umberhold**, the player spends the majority of their time in a loop consisting of four core activities:

* **Grid Exploration:** Navigating 1st-person, $26 \times 26$ regional maps to uncover coordinates ($A1-Z26$). This involves mapping terrain, triggering "Set-Piece" narrative events, and finding transit points between different climates (e.g., muddy south to icy north).
* **Tactical Combat:** Engaging in frequent turn-based battles using a 4-rank linear system. Players manage a 6-character party, utilizing **Range (1–3)** to target enemies across 6-slot rows while reacting to "Advance" movements from melee monsters.
* **Power Progression:** Collecting gold and experience points to reach the Level 10 cap. This includes gathering **Uncommon/Rare magic items** from the grid to increase party power and paying for essential services like **Resurrection** ($500gp \times Lvl$) or healing.
* **Quest Completion:** Advancing the **Main Quest** (finding the Lord Patriarch and the High Priest) while simultaneously completing various **Side Quests** to earn the gold necessary for survival and gear upgrades.


::

What makes this game different from others? 

Unlike typical dungeon crawlers that offer minimal plot, **Umberhold** distinguishes itself with an expansive, deeply integrated narrative. The world is dark and dangerous, and because the game can only be saved at an Inn, the stakes for every excursion are significantly higher.


::


The emotional core of **Umberhold** is defined by the high-contrast cycle between the **fear of loss** and the **jubilation of success**. 

### **1. Fear of Loss**
The game creates a persistent sense of dread through its restrictive systems. Because you can **only save at an Inn**, every step taken into a $26 \times 26$ grid is a gamble. 
* **The Stakes:** High-level characters represent a massive investment of time and gold. 
* **The Penalty:** With a **25% base resurrection failure rate**, death is not a temporary setback but a potential permanent loss of a teammate.
* **The Environment:** Moving through dark, dangerous climates with limited resources ensures the player is always aware of how far they are from the safety of the last save point.

### **2. Jubilation at Success**
Because the risks are so high, the rewards feel earned rather than given.
* **Survival as Victory:** Successfully returning to an Inn after a deep trek into a hazardous region provides a massive sense of relief and accomplishment.
* **Tactical Triumph:** Overcoming a "Gigantic" 4-slot boss using precise **Range (1–3)** positioning and limited spell slots creates a peak "high" that is only possible because the threat of failure was real.
* **Power Milestones:** Finding a rare magical item or reaching a new Level (up to the cap of 10) feels significant because the journey to acquire those assets was genuinely dangerous.



### **3. The "Tension Loop"**
The player spends the majority of their time in a state of calculated tension. The deep, integrated story provides the motivation to keep pushing forward, while the "dark and dangerous" mechanics ensure that every victory, no matter how small, is met with genuine jubilation.


::



## **Umberhold Core Gameplay Loop**

### **Main Loop**
The primary cycle is **Explore → Fight → Loot → Upgrade → Repeat**. Players venture from the safety of an Inn into dangerous $26 \times 26$ regional grids to face progressively difficult encounters, returning to town to secure their progress and power up.

### **Loop Duration**
A single session or loop cycle is highly flexible, ranging from a **15-minute** quick excursion to a **4-hour** deep crawl into a major dungeon or new region.

### **Player Retention**
The drive to return is fueled by constant **Progression**. Players are motivated by the immediate rewards of gaining the next level (up to level 10), finding a better sword, or mastering a more powerful spell, all while pushing to complete the **Main Quest**.

### **Loop Nature**
The loop is a hybrid of **Strategy-Based** mechanics and **Story-Driven** progression. 
* **Strategy:** Success depends on managing 4-rank tactical combat, 6-slot enemy formations, and the high stakes of a save system restricted to Inns. 
* **Story:** Unlike typical limited-plot crawlers, the deep, integrated narrative provides the ultimate purpose for every cycle of exploration and combat.














\page


## **Umberhold: Targeting & Interaction System**

The combat interface combines **Keyboard Hotkeys** with **Mouse Targeting** to manage the tactical rank-based battlefield.

---

### **I. Input & Command Flow**
* **Step 1: Trigger Action:** The player initiates an action using dedicated keyboard hotkeys.
    * **Attack (A):** Opens the melee/ranged attack menu.
    * **Cast Spell (C):** Opens the magic menu, featuring a list of **recently cast spells** for quick selection.
* **Step 2: Selection:** The player chooses the specific attack or spell from the **dropdown boxes**.
* **Step 3: Target (Mouse Click):** Once the action is triggered, the player **Left-Clicks** on a monster portrait within the 6-slot enemy ranks to select their target.
    * **Range Validation:** The system checks the character's **Range (1–3)** against the monster's rank (Front or Rear) before confirming the click.

---

### **II. Tactical Combat Controls**
| Component | Method | Description |
| :--- | :--- | :--- |
| **Movement** | **WASD** | 1st-person, step-based navigation on the $26 \times 26$ grid. |
| **Action Trigger** | **A** or **C** | Hotkeys to open Attack or Spell dropdowns. |
| **Targeting** | **Left-Click** | Manual selection of monsters in the 6-slot formation. |
| **Positioning** | **Stationary** | Players **do not move or dash** in combat; only monsters move/advance. |
| **Confirmation** | **Instant** | Actions are turn-based and executed immediately upon target selection. |

---

### **III. World Interaction & NPCs**
* **Intelligent NPCs:** Interaction is handled via dialogue dropdowns. NPCs (like Bartholomew or Wymarc) possess their own intelligence and react to quest progression.
* **Coordinate Interaction:** Players use the mouse to interact with chests, environmental triggers, or transit points at specific coordinates ($A1-Z26$).
* **No Building:** The player's actions are focused on exploration, combat, and dialogue; there are no mechanics for building structures.

---

### **IV. High-Stakes Experience**
* **Save System:** Progress can **only be saved at an Inn**, reinforcing the "Fear of Loss" and "Jubilation at Success" emotional cycle.
* **The Loop:** Adventuring into regional grids → Fighting → Collecting loot/gold → Returning to the Inn to save and upgrade.

Would you like me to document the specific "Range 1–3" validation rules for Left-Click targeting?





\page



## **Umberhold: Player Systems & Vitality**

In **Umberhold**, the player is defined by a rigid resource-management system based on **5E D&D foundations** but with significantly higher stakes and a slower progression curve.

---

### **I. Health & Mortality**
* **Hit Points (HP):** Characters have a defined **Current** and **Maximum** HP.
* **Death State:** If a character reaches **0 HP**, they die immediately. 
* **Visual Status:** Upon death, the character is automatically moved to the **rear of the party**. Their portrait is replaced by a **shadowed silhouette** with a **skull for a face**.
* **Recovery:** Restoration of life is only possible through the **Solcine Chantry** in town (subject to the **failure rate**).

---

### **II. Energy & Resource Systems**
* **No Stamina:** Actions are not restricted by physical exhaustion.
* **No Mana:** The game does not use a mana pool.
* **Spell Slots:** Spellcasters follow the **5E Spell Slot system**, where a fixed number of slots are expended and only regained during a **Long Rest at an Inn**.
* **No Survival Stats:** There are no mechanics for hunger, thirst, or environmental survival stats.

---

### **III. Progression & Leveling**
* **Level Cap:** Characters progress from **Level 1 to Level 10 (Maximum)**.
* **Experience (XP) Curve:** Leveling is significantly slower than standard 5E, requiring **5x the standard experience** to reach the next level.
* **Upgrades:** Progression is marked by gaining new spells, increased HP, and better proficiency in the 4-rank tactical combat system.

---

### **IV. Inventory & Encumbrance**
The inventory system is designed to be restrictive to increase the tension of exploration.
* **Limited by Encumbrance:** Characters have a hard weight limit. 
* **No Overloading:** Once a character reaches their maximum weight capacity, they **cannot** pick up more items. 
* **No Stacking:** Items are individual and **do not stack** (e.g., each potion or arrow takes up its own space/weight calculation).

---

### **V. Core Systems Summary**

| System | Mechanic | Detail |
| :--- | :--- | :--- |
| **Vitality** | **HP** | Death at 0 HP; Portrait becomes a skull/shadow. |
| **Magic** | **Spell Slots** | Recharges only at an Inn; no mana used. |
| **Progression** | **XP x5** | Slower Level 1–10 curve than 5E. |
| **Inventory** | **Hard Cap** | No stacking; encumbrance prevents further looting. |
| **Saving** | **Inn Only** | High-stakes excursions with no mid-grid saving. |

Would you like me to detail the specific **Spell Slot table** for a Level 1–10 caster under this x5 XP progression?


\page





## **Umberhold: Challenge & Difficulty**

The difficulty in **Umberhold** is driven by tactical combat and resource management rather than mechanical gimmicks or time-based stress.

---

### **I. Primary Obstacles & Scaling**
* **Monster Strength:** The main push against the player comes from progressively more powerful enemies. As you move into new regions (from the muddy South toward the icy North), monster stats, rank abilities, and slot sizes increase.
* **Gearing & Leveling:** Difficulty scales such that players **must** level up (on the $5\times$ XP curve) and find superior equipment to survive the next area, dungeon, or section of the game.
* **No Puzzles:** There are no time-wasting or annoying puzzles to solve. The challenge is strictly found in combat strategy and party progression.
* **No Time Pressure:** Players can take as long as they need to explore a $26 \times 26$ grid or decide on a move in combat; there are no ticking clocks.

---

### **II. Failure & Death State**
* **The Graveyard Screen:** If all six characters in the party reach **0 HP**, the game transitions to a dedicated graveyard screen.
* **Defeat Message:** The words **"You have been defeated"** appear on the screen.
* **Loading:** An option is provided to **Load a Saved Game**. Selecting this reverts the game entirely to the last point saved at an **Inn**.
* **No Permanent Consequences:** While the "Fear of Loss" is a core emotion during a run, loading a save ensures that there are no permanent mechanical penalties or lost progress beyond what happened after the last save.

---

### **III. Item Mechanics & Management**
* **No Durability:** Items are permanent; they do not break, lose durability, or degrade over time.
* **Trading:** Items can be traded between characters by **clicking and drag-dropping** the item onto another character's portrait.
* **Disposal:** Items can be sold to NPCs (like Oswaldine) or dropped if the character reaches their **Encumbrance** limit.
* **Item Security:** Items are not lost upon individual character death (unless the entire party is defeated and you choose not to reload).

---

### **IV. Challenge Summary Table**

| Feature | Mechanic | Detail |
| :--- | :--- | :--- |
| **Scaling** | **Stat-Based** | Monsters grow stronger as you progress North. |
| **Obstacles** | **Combat/Gear** | Success requires level-ups and magic items. |
| **Puzzles** | **None** | No time-wasting or annoying puzzles. |
| **Total Wipe** | **Graveyard** | Screen appears with "You have been defeated." |
| **Reload** | **Inn Save** | Reverts game state to the last Inn save point. |
| **Durability** | **Infinite** | Items never break or require repair. |

\page



###  **AI & Enemy Behavior**

The combat AI in **Umberhold** follows a specific tactical logic based on the monster's role (Melee vs. Ranged). 

---

#### **1. Movement & Rank Logic**
Enemies do not simply rush forward; they maintain their tactical advantage based on their attack type:

* **Melee Strong Monsters (Front-Fill):** These aggressive units automatically **"Advance"** to fill any empty slots in the **Enemy Front Rank** as a free action on their turn. 
* **Ranged Monsters (Static/Rear):** Monsters equipped with **spells or bows** (Range 2–3) will **remain in the Enemy Rear Rank**. They will not advance into the Front Rank.
* **Tactical Depth:** This creates a split-threat environment where the player must manage the advancing melee wall while targeting the stationary casters and archers in the back.

---

#### **2. Encounter Structure**
* **Random Encounters:** Triggered by a percentage chance during any grid move on the $26 \times 26$ map.
* **Set-Piece Encounters:** Scripted battles at fixed coordinates. These are harder, advance the **Main Quest**, and feature **cut-scenes with dialogue**.
* **Boss Hierarchy:** * **Sub-Bosses:** 2–3 smaller, unique bosses per dungeon level.
    * **The "Big" Boss:** 1 major boss per level (often **Gigantic 4-slot**) with unique mechanics and story-heavy dialogue.

---

#### **3. Interaction & Parley**
* **Hostility:** Most monsters are aggressive and initiate combat immediately.
* **Parley:** A few monsters or NPCs can be spoken to via the **Intelligent NPC** system, allowing for dialogue-driven resolutions or story reveals.

---

### **VII. Core Combat Interface (Updated)**

| Action | Method | Description |
| :--- | :--- | :--- |
| **Turn Start** | **Auto-Popup** | Dropdown boxes (Attack, Cast Spell, Use Item, Dodge, Equip Another Weapon) appear. |
| **Attack/Cast** | **A or C Keys** | Simple Keys to  |
| **Targeting** | **Left-Click** | Manual selection of a monster portrait in its 6-slot rank. |
| **Range Check** | **Automatic** | Validates Range (1–3) before the action executes. |
| **Dodge** | **Selection** | Attacks are made at disadvantage (a 5E mechanic) agaisnt a dodging creature/character. |

---

### **VIII. Failure & Save System**
* **The Graveyard:** A total party wipe triggers a graveyard screen with the words: **"You have been defeated."**
* **Reloading:** You can load your last **Inn Save**. This reverts the game state entirely, but items are never lost or broken through durability.






\page


### **II. World Navigation & Travel**
* **Local Travel:** Players navigate the $26 \times 26$ grid using **WASD** in a 1st-person "step" view.
* **Regional Travel:** Movement between the 9 lands is **hand-waved on a larger regional map**. For example, a path through the wilderness connects the starting area of **Umberhold** to a neighboring town in an adjacent region.
* **Gated Progression:** While the world is not strictly "level-locked," the difficulty of monsters scales sharply. It is mechanically difficult to survive in a new land unless characters have gained sufficient levels and equipment from the previous area.

---

### **III. Save & Checkpoint System**
* **Inn-Only Saving:** There are no mid-dungeon checkpoints or auto-saves. Progress, gold, and experience can **only be secured by reaching an Inn** within a settlement.
* **The Stakes:** This restriction reinforces the "Fear of Loss," as a total party wipe sends the player to the **Graveyard Screen** ("You have been defeated"), requiring a reload from the last Inn save.

---

### **IV. Replayability & Persistence**
* **Replayable Grids:** Players can revisit and re-traverse any region or dungeon they have previously cleared.
* **Encounter Persistence:** * **Random Encounters:** These continue to trigger as the player moves, allowing for necessary $5\times$ XP grinding and gold collection.
    * **Set-Piece Encounters:** Major story battles and scripted events are **one-off**. Once a boss or narrative guardian is defeated, they do not respawn, though the location remains accessible.

---

### **V. World Structure Summary**

| Feature | Mechanic | Description |
| :--- | :--- | :--- |
| **Scope** | **9 Regions** | Each with a town, a dungeon, and a $26 \times 26$ grid. |
| **Progression** | **Regional Map** | Hand-waved travel between settlements/lands. |
| **Scaling** | **Soft-Lock** | Survival is dependent on Level (1–10) and Gear. |
| **Saves** | **Inn Only** | Manual saves at settlements (inns) only; high-stakes trekking. |
| **Encounters** | **Hybrid** | Random battles are infinite; Set-Pieces are unique. |

---

### **VI. Character System (Reminder)**
* **HP:** Current/Max. 0 HP = Death (Shadow/Skull portrait).
* **Classes:** Spellcasters (Slots as per 5E).
* **Inventory:** Limited by **Encumbrance**. Items are permanent and tradable via **Click-and-Drag**.



\page

## **Umberhold: Progression & Rewards**

The progression system in **Umberhold** is designed to provide a constant sense of growth, shifting from a vulnerable Level 1 party to a powerhouse capable of slaying the **Lich King**.

---

### **I. Character Growth & Upgrades**
* **Gaining Levels (1–10):** Leveling follows a slower $5\times$ XP curve. Each level provides:
    * **HP Increases:** Raising both Current and Maximum Hit Points.
    * **New Skills/Abilities:** Characters gain 5e-based class features and tactical upgrades.
    * **Spell Slots:** Spellcasters unlock higher-tier slots, allowing for more powerful magic (recharged only at an Inn).
* **Equipment & Gear:** Progression is heavily gear-dependent. Players seek out:
    * **Powerful Magic Items:** Finding Uncommon or Rare items within the $26 \times 26$ grids provides essential stat boosts and unique effects.
    * **Permanent Utility:** Since items have **no durability** and never break, a "better sword" is a permanent power spike for the party.

---

### **II. Reward Systems**
* **Loot & Gold:** Defeating monsters and exploring coordinates yields gold and items. Gold is the primary resource for **Resurrection** ($500gp \times Lvl$) and purchasing high-tier consumables at the Alchemist’s Mortar.
* **Rare Rewards:** While common loot is found in random encounters, **Rare items** are often hidden at specific coordinates or guarded by **Set-Piece bosses**.
* **Story Unlocks:** Completing questlines (like finding High Priest Pancras) unlocks access to new regions, advanced shops, and the final path to the **Necropolis of Malakor**.

---

### **III. Progression Structure**
* **Main Questline:** The path is **linear** and narrative-driven. The party must advance through the 9 regions, defeating the "Big" boss of each land to move closer to the frozen North.
* **Side Content:** "Culling Contracts" from the Bailiff’s Desk provide non-linear opportunities to earn the gold and XP necessary to overcome the main quest's difficulty spikes.
* **The Ultimate Goal:** The entire loop of explore $\rightarrow$ fight $\rightarrow$ loot $\rightarrow$ upgrade is focused on a single objective: **Slaying the Lich King**.

---

### **IV. Progression Summary Table**

| Reward Type | Mechanic | Player Impact |
| :--- | :--- | :--- |
| **Experience** | **$5\times$ XP Curve** | Higher HP and 5e-style class abilities. |
| **Equipment** | **Permanent Items** | Better weapons/armor; no durability loss. |
| **Magic** | **Spell Slots** | Access to more powerful, high-impact spells. |
| **Economy** | **Gold Accumulation** | Funds for healing, resurrection, and gear. |
| **Narrative** | **Quest Milestones** | New regions and the finale against the Lich King. |

---

### **V. The "Hook"**
The player keeps playing to satisfy the **Jubilation at Success**. Every level gained and every rare item found makes the **dark and dangerous** world slightly more manageable, driving the party to take one more trek out from the Inn into the unknown.















::





Win & Lose Conditions
The Win Condition: Successfully navigating all 9 regions to reach the frozen North and slaying the Lich King in the final encounter.

The Lose Condition: A total party wipe where all six characters reach 0 HP through combat or environmental mishap.

Result: The Graveyard Screen appears with the message "You have been defeated," requiring the player to reload their last Inn Save.




\page


## **Umberhold: Feedback & Juice**

In **Umberhold**, high-fidelity animations and sound effects are essential for making the stationary, menu-based combat feel visceral and impactful.

---

### **I. Visual Feedback & Animations**
The game uses specific animations to communicate the weight of every action on the 4-rank grid:
* **Combat Impact:** * When an Ogre attacks, players see a **club smash** animation that fills the screen.
    * Successful hits result in **blood spatters** across the target's portrait or the rank slot.
    * Status effects are visually distinct: **a poisoned character's portrait has a green tinge**.

* **Death State:** The most significant visual indicator is the **shadowed portrait with a skull face**, showing a character has reached 0 HP and moved to the Rear.

---

### **II. Audio Design (The "Soundscape of Dread")**
Sound effects provide the primary sensory feedback for the success or failure of player actions:
* **Spells:** A fireball doesn't just "pop"—it **sounds like an inferno**, providing an auditory reward for spending a limited 5E spell slot.
* **Physical Combat:** Heavy weapons produce a thud or metallic clang, while critical hits might trigger a unique, sharper sound effect.
* **UI Feedback:** Navigating the **dropdown boxes** and selecting "A" (Attack) or "C" (Cast) provides tactile audio clicks to confirm inputs.

---

### **III. Success & Danger Indicators**
* **Damage Numbers:** Visual indicators pop up over character portraits and enemies to show the exact HP lost. Red numbers for damage and green for healing.
* **Turn Notifications:** A turn order (initiative from highest to lowest) is represented by small portraits of the characters and enemies on the left side of the screen during combat.
* **The Graveyard Screen:** The ultimate "wrong" move results in the screen fading to the graveyard with the high-impact text: **"You have been defeated."**






\page



##### Armor Statistics

| Item Name       | Cost (GP) | AC / Damage      | Weight (Stones) | Init. Mod | Min STR | Notes           |
| --------------- | --------- | ---------------- | --------------- | --------- | ------- | --------------- |
| Padded Armor    | 5         | 11 + AGI         | 8               | 0         | -       | Stealth Disadv. |
| Leather Armor   | 10        | 11 + AGI         | 10              | 0         | -       | Basic Light     |
| Studded Leather | 45        | 12 + AGI         | 13              | 0         | -       | Best Light      |
| Hide Armor      | 10        | 12 + AGI (Max 2) | 12              | -1        | -       | Medium          |
| Chain Shirt     | 50        | 13 + AGI (Max 2) | 20              | -1        | -       | Medium          |
| Scale Mail      | 50        | 14 + AGI (Max 2) | 45              | -2        | -       | Medium          |
| Breastplate     | 400       | 14 + AGI (Max 2) | 20              | -1        | -       | Medium          |
| Half Plate      | 750       | 15 + AGI (Max 2) | 40              | -2        | -       | Medium          |
| Ring Mail       | 30        | 14 (Flat)        | 40              | -2        | -       | Heavy           |
| Chain Mail      | 75        | 16 (Flat)        | 55              | -3        | 13      | Heavy           |
| Splint Armor    | 200       | 17 (Flat)        | 60              | -4        | 15      | Heavy           |
| Plate Armor     | 1500      | 18 (Flat)        | 65              | -5        | 15      | Heavy           |
| Shield          | 10        | +2 AC            | 6               | -1        | -       | Off-Hand        |


\page


##### Weapon Statistics

| Item Name      | Cost (GP) | Damage | Weight (Stones) | Init. Mod | Min STR | Range | Notes             |
| -------------- | --------- | ----------- | --------------- | --------- | ------- | ----- | ----------------- |
| Dagger         | 2         | 1d4         | 1               | +2        | -       | 1     | Finesse, 1-handed       |
| Shortsword     | 10        | 1d6         | 2               | +2        | -       | 1     | Finesse, 1-handed      |
| Scimitar       | 25        | 1d6         | 3               | +1        | -       | 1     | Finesse, 1-handed       |
| Mace           | 5         | 1d6         | 4               | 0         | -       | 1     | 1-handed            |
| Rapier         | 25        | 1d8         | 2               | 0         | -       | 1     | Finesse, 1-handed             |
| Katana         | 25        | 1d8         | 2               | 0         | -       | 1     | Finesse, 1-handed             |
| Longsword      | 15        | 1d8         | 3               | -1        | -       | 1     | 1-handed                   |
| Battleaxe      | 10        | 1d8         | 4               | -1        | -       | 1     | 1-handed                   |
| Greatsword     | 50        | 2d6         | 6               | -3        | 10       | 1     | 2-Handed   |
| Greataxe       | 30        | 1d12        | 7               | -3        | 11       | 1     | 2-Handed   |
| Maul           | 10        | 2d6         | 10              | -4        | 12       | 1     | 2-Handed   |
| Halberd        | 20        | 1d10        | 6               | -4        | 10       | 2     | 2-Handed   |
| Boar Spear     | 15        | 1d10        | 5               | -2        | -       | 2     | 2-Handed   |
| Sling          | 0.1       | 1d4         | 0               | +2        | -       | 3     | 2-handed                 |
| Shortbow       | 25        | 1d6         | 2               | +1        | -       | 3     | 2-Handed          |
| Light Crossbow | 25        | 1d8         | 5               | -1        | -       | 3     | 2-Handed |
| Longbow        | 50        | 1d8         | 2               | -2        | -       | 3     | 2-Handed          |
| Heavy Crossbow | 50        | 1d10        | 18              | -4        | 14       | 3     | 2-Handed |




**Finesse:** A weapon with the Finesse trait allows you to use either Strength or Agility for attack and damage rolls, choosing whichever bonus is higher.





\page


##### Lockpicking


This is the finalized, logical architecture for the **Chest and Lockpicking System** in **Umberhold**. It integrates the visual transition, the high-stakes "one-shot" mechanics, and the technical skill formulas into a single cohesive design.

---

## 📦 The Loot Sequence

### 🖼️ Visual Transition & Persistence
* **Trigger:** A chest is not guaranteed after every fight. If an encounter triggers a loot drop, the **20x20 Combat Grid** dissolves and the screen switches **immediately** to a high-detail illustration of the chest.
* **One-Shot Event:** This is a localized event. Once the screen is closed—whether by opening the chest, jamming all locks, or selecting **Leave Alone**—the chest is **removed from the game world forever** and cannot be revisited.

---

### 🧰 The Chest Interaction Interface
From the chest illustration screen, the player manages the following options:

| Option | Logic & Consequence |
| :--- | :--- |
| **1. Open** | Attempt to lift the lid. If **Locked**, it fails. If **Trapped**, the trap triggers before the chest opens. |
| **2. Examine** | Select a character to perform a **Detect Traps** check. Success reveals trap and lock status. **Failure:** Displays **"You can't find a trap."** |
| **3. Remove Trap** | Attempt to disarm a *detected* trap. **Success:** Trap removed. **Failure:** Trap triggers immediately. |
| **4. Pick Lock** | Select a character for a single attempt. Failure jams the lock for that specific character. |
| **5. Cast Spell** | Use utility spells (e.g., *Find Traps* for auto-reveal or *Knock* for auto-unlock). |
| **6. Use Item** | Use unique inventory items (e.g., **Skeleton Keys** or **Disarming Kits**). |
| **7. Leave Alone** | **Exits the screen; the chest is gone forever.** |

---

## 🔐 Lockpicking Mechanics

### 🎲 The Skill Check
The game automatically identifies the character's best available tools and calculates the roll using the following formula:

$$1d20 + \text{AGI Modifier} + \text{Proficiency Bonus} + \text{Item Bonus}$$

* **Proficiency Scale:** **+2** (Levels 1–4), **+3** (Levels 5–8), **+4** (Levels 9–10).
* **Persistent Tools:** Lockpicks **cannot break**. They are permanent utility items.
* **One-Shot Rule:** Every character in the party gets exactly **one attempt**. If they fail, their unique ID is flagged, and they cannot attempt that specific lock again. There is no "resting" to reset the check.

### 📊 Lock Difficulty (DC) Table

| Difficulty | Lock DC | Typical Location |
| :--- | :--- | :--- |
| **Crude** | **5** | Rusted iron gates, cellar doors, peasant chests. |
| **Simple** | **10** | Standard merchant lockboxes, interior tavern doors. |
| **Complex** | **15** | City guard armories, noble household jewelry boxes. |
| **Intricate** | **20** | High-security vault drawers, royal archives. |
| **Diabolical** | **25** | Ancient tomb seals, legendary relic chambers. |

---

## 💥 Trap Hazards

### 🔍 Search Uncertainty
If an **Examine** check fails, the message is always **"You can't find a trap."** This message is identical whether the chest is safe or if a trap was simply missed. This forces the player to decide if they trust their current scout or if they should have a second character re-examine the chest before risking the **Open** command.

### 🛡️ Area of Effect (AoE)
* **Personal Traps:** (e.g., Poison Needle) Visual effect flashes over the portrait of the character who performed the action. Only that character takes damage.
* **Party-Wide Traps:** (e.g., Gas Cloud, Magical Explosion) A full-screen overlay covers the chest illustration. Every party member takes damage and status effects simultaneously.

---


\page


##### Race


| Race       | Stat Bonuses                     | Secondary Perks & Resistances                                                            |
| ---------- | -------------------------------- | ---------------------------------------------------------------------------------------- |
| Human (Medium)      | +1 to four random stats (max 18) | Versatility: Highly adaptable starting array.                                            |
| Everkin (Medium)    | +1 Agility, +1 Intellect         | Archer’s Eye: +1 to hit with bows; crits on 19–20 with a bow; advantage vs. sleep and charm effects. |
| Deepfolk (Medium)   | +1 Constitution, +1 Strength     | Dwarven Toughness: +1 HP per level; +4 bonus to saving throws vs. poison.                |
| Stoutlings (Small) | +1 Luck, +1 Agility              | Small & Stealthy: +4 to lockpicking; +2 to all saving throws.                            |
| Tinkerfolk (Small) | +1 Intellect, +1 Luck            | Artifact Mastery: On a natural 20 with a damaging magic item, the effect is doubled.     |
| Hillkin (half-ogres, Large) |  +1 Constitution, +1 Strength           | Base AC: 11 (leathery hide); -4 to Agility saving throws due to size.    |




\page




##### Character Creation Process



Sex (male of female): This choice has no mechanical effect on gameplay.

:

Race
:

Vocation
:
Roll Statistics: Roll 3d6 for each of the seven statistics. The results must be used as rolled and cannot be reassigned to different attributes.

:
:: Strength
::Constitution
::Agility
::Intellect
::Wisdom
::Personality (this is Charisma in 5e)
::Luck


:
Hit points (characters begin with **maximum** hit points at first level an in 5E)
:
Starting Gold - roll 10d20
:

At this point, choose whether to keep or disard the character.
:
If the player chooses to keep the character, the final two choices are Class and Name.





\page
##### Vocations

Vocations are character backgrounds, and one is chosen at character creation.  

| Vocation          | Summary                                                  | Starting Boon (5e Mechanics)                                                                    |
| ----------------- | -------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Whipping Boy/Girl | Received the physical lashings earned by noble children. | **Hardened:** 50% chance to turn any critical hit suffered into a normal hit.     |
| Poison Taster     | Sampled dishes for paranoid lords to detect toxins.      | **Internal Fortitude:** You have Advantage on Saving Throws against being Poisoned. Additionally, poison damage is reduced by 25%.             |
| Gong Farmer       | Cleared human waste from cesspits beneath the village.   | **Stench-Blind:** You are immune to the Poisoned condition caused by foul odors or gases.       |
| Sin Eater         | Ritually “consumed” the sins of the dying via bread.     | **Soul-Scarred:** +4 to Wisdom saving throws.                 |
| Leech Collector   | Waded through marshes using their own legs as bait.      | **Clot-Quick:** When rolling hit points on level-up, a result of 1 is never kept. If a 1 is rolled, reroll the die until a higher result is obtained.    |
| Rat Catcher       | Hunted vermin in the lightless, infested sewers.         | **Vermin-Sense:** +1 Agility.    |
| Mudlark           | Scavenged riverbeds at low tide for scrap.               | **Eagle-Eye:** Your eye is keen; you roll Initiative at +4.       |
| Plague Burier     | Tossed the victims of the “soot-cough” into mass pits.   | **Morbid Touch:** You have Resistance to Necrotic damage.                                       |
| Knacker           | Rendered old livestock into glue, tallow, and hide.      | **Heavy-Handed:** You gain a +1 bonus to damage rolls with all melee weapons.                 |
| Toad-Eater        | Ate live toads to prove a charlatan’s “miracle cure.”    | **Iron Gut:** You are resistant to poison damage (resistance means you take half damage).             |
| Chimney Sweep     | Scoured soot from tight, lightless, scorching flues.     | **Limber:** +4 to Dexterity saving throws.                    |
| Gibbet-Cleaner    | Scrubbed the remains of criminals from iron cages.       | **Death-Calloused:** You have Advantage on Saving Throws against being Frightened.  |






\page


### **The Resurrection Formula**
In the **Solcine Chantry**, Acolyte Gidney calculates the survival of a fallen hero using the following logic:

$$\text{Resurrection Failure Rate} = 20\% - 1\% \times \text{Constitution Score}$$
*(Minimum failure rate of 1%)*

---

### **Impact on Gameplay**
This scaling creates a massive strategic divide between high-fortitude survivors and fragile spellcasters:

* **The Fragile Mage (CON 8):** Faces a **12% failure rate**. Death is a significant gamble.
* **The Average Hero (CON 10):** Faces a **10% failure rate**.
* **The Stalwart Fighter (CON 16):** Faces a **4% failure rate**. Much more likely to return from the "Skull/Shadow" state.
* **The Paragon (CON 19+):** Hits the **1% minimum floor**. Even for the toughest heroes, there is always a sliver of risk—death is never 100% reversible.

---

### **NPC Interaction: Acolyte Gidney**
When you bring a body to the Chantry, Gidney’s dialogue will reflect these odds based on the character's **Constitution**:

> **Low CON:** *"Their spirit clings to this world like a dying candle in a gale, traveler. I shall try, but the thread is frayed..."*
> 
> **High CON:** *"This one has a stubborn marrow. The flesh is broken, but the will to live is a bonfire. Stand back."*

---

### **Updated Systems Summary**

| System | Mechanic | Constraint |
| :--- | :--- | :--- |
| **Recovery** | **Resurrection** | $20\% - \text{CON}\%$ (Min 1%). |
| **Cost** | **Gold Payment** | $500\text{gp} \times \text{Character Level}$. |
| **Vocation Bonus** | **Gibbet-Cleaner** | Grants **Advantage** on the first Death Save before Gidney is even needed. |
| **Consequence** | **Permanent Loss** | If the roll fails, the character is gone forever. Reverting requires loading an **Inn Save**. |

Would you like me to create a **Resurrection Table** showing the exact failure percentages for every Constitution score from 3 to 20?
\page






| Class (name in brackets is the 5E equivilent)       | Primary Attributes | Level 10 Title | Role & Core Mechanic                                                                                            |
| ------------ | ------------------ | -------------- | --------------------------------------------------------------------------------------------------------------- |
| Shadowman (rogue)   | AGI / LCK          | Dread-Shade    | Striker: High-initiative dual-wielder. Uses Low Blow for burst damage and harvests venom from carcasses. Able to open locks and find and remove traps.       |
| Man-at-Arms (fighter)  | STR / CON          | Warlord        | Tank: Front-line anchor. |
| Warden (ranger)       | AGI / PIE          | Nature-Wraith  | Scout: Excels at point-blank archery. A half caster.                  |
| Hedge Wizard (wizard) | INT                | Black Archon   | Full caster: rear-rank blaster, elemental specialist, and anti-magic spellcaster.           |
| Friar (cleric)        | PIE                | Saint of the Last Rite | Full caster: healer, undead controller, and quarterstaff battle-priest.         |
| Crusader (paladin)     | STR / PIE          | Divine Exemplar | Front-rank holy bruiser, aura support, and anti-evil half caster.         |
| Troubadour (bard)   | PRE / LCK          | Maestro of Ruin | Support half caster. Uses sustained songs and social talent to bolster allies and hinder enemies.   |

\page

An example of skills gained by leveling.

Shadowman (or Shadowlady if the character is female)


| Level | Title         | Feature / Growth Highlights                   |
| ----- | ------------- | --------------------------------------------- |
| 1     | Guttersnipe   | Slip into Shadows, Vigilance, Low Blow (1d6), Open Locks, Find and Remove Traps |
| 2     | Footpad       | Anatomical Study (19–20 Crit)                 |
| 3     | Cut-Purse     | Uncapped Attribute Growth, Dual Wield                |
| 4     | Bravo         | Riposte (+1 AC)                               |
| 5     | Venom-Drinker | Venom Harvester, Low Blow (2d6)               |
| 6     | Thug-Lord     | Dirty Fighting             |
| 7     | Night-Stalker | Uncapped Attribute Growth                     |
| 8     | Shadow-Dancer | Evasion (No damage on AGI saves)              |
| 9     | Ghost-Hand    | Master of Shadows (Advantage on Stealth checks)      |
| 10    | Dread-Shade   | Uncapped Attribute, Low Blow (3d6), Master Harvester            |





**Open Locks:** Only a Shadowman has this ability. A lockpicking check uses an Agility check plus the character’s Proficiency Bonus, as in 5E, and requires Thieves’ Tools. Certain Thieves’ Tools may grant an additional bonus to this roll. Each lock may be attempted only once; a failed attempt means the lock must be bypassed by other means.


**Find and Remove Traps:** Only a Shadowman has this ability. They require a set of Thieves’ Tools to detect, disable, or safely bypass mechanical traps. Detecting a trap uses a Perception check plus Proficiency Bonus, while disabling it uses an Agility check plus Proficiency Bonus.




**Slip into Shadows:** You vanish into shadow and reappear where the enemy least expects. If you choose this option on your turn in combat, make a Stealth check against the highest enemy passive Perception. On a success, you may attack any enemy in any rank, with advantage (roll twice to attack and take the highest roll); if you hit, you deal extra Low Blow damage, which increases as you gain levels. After the attack, you return to your normal position in the party ranks. If you fail to enter Stealth (you are detected), you lose your attack but suffer no additional consequences. 


**Low Blow:** You deal extra damage to targets that don't see you coming (see Slip into Shadows). 


**Vigilance:** +4 to all Initiative rolls.


**Anatomical Study:** Your attacks now crit (double dice damage) on a natural roll of 19-20.

**Uncapped Attribute Growth:** You can increase one statistic score by 2, or two by one (as per 5E rules).

**Dual Wield:** You may now use a melee weapon in your off-hand as long as it is lighter than your main hand. You can attack with this weapon each turn as a Bonus Action.

**Riposte:** When dual wielding, your AC is +1.

**Venom Harvester:** You may make a DC 15 Survival check to harvest poison from a poisonous creature. No special tools are required, and you are assumed to carry small phials for storage. On a success, you harvest 1d2 doses. As an action, you may apply one dose to a melee weapon; the poison is single-use, expended after the first successful hit and must be reapplied to poison the weapon again. If you fail the harvesting check by 5 or more, you are affected by the poison.

**Dirty Fighting:** You know where to strike to open surface blood vessels and cause bleeding. When you hit, the target takes one additional die of damage—matching the damage die you rolled—at the start of the enemy’s next turn as bleeding damage.

**Evasion:** If you succeed on an Agility saving throw against a spell or effect that would normally deal half damage on a success (such as a fireball or a creature’s breath weapon), you instead take no damage.

**Master of Shadows:** You now have advantage on all Stealth checks.

**Master Harvester:** On a successful Survival check to harvest poison from a poisonous creature, you now harvest 1d4 doses, and you can never poison yourself while harvesting a poisonous creature.

\page

Hedge Wizard

| Level | Title              | Feature / Growth Highlights                                         |
| ----- | ------------------ | ------------------------------------------------------------------- |
| 1     | Mire Initiate      | Spellcasting (Intellect)                                            |
| 2     | Ash Whisperer      | Blackwell Casting (chance to not expend spell slot)                 |
| 3     | Grave Scholar      | Uncapped Attribute Growth                                           |
| 4     | Relic Leech        | Charge Siphon (chance to not expend item charges)                   |
| 5     | Blight Channeler   | Elemental Mastery (Pyromancer, Cryomancer, Stormcaller, Venomancer) |
| 6     | Hex Savant         | Spell Mastery (1st-level spell becomes a cantrip)                   |
| 7     | Dread Arcanist     | Uncapped Attribute Growth                                           |
| 8     | Sanguine Channeler | Vampiric Conduit (heal from elemental kills)                        |
| 9     | Veilbreaker        | Arcane Defiance (chance to resist spells entirely)                  |
| 10    | Black Archon       | Cataclysm Casting (spell crits), Spell Reflection                   |

**Spellcasting:** You are a full caster. Your spellcasting ability is Intellect.

**Blackwell Casting:** When you cast a spell, there is a 5% + 1% per point of your Luck modifier chance that the spell does not consume a spell slot.

**Uncapped Attribute Growth:** You can permanently increase two attributes by 1 point each, or increase one attribute by 2 points.

**Charge Siphon:** When you use an item with charges, there is a 10% + 1% per point of your Luck modifier chance that the charge is not expended.

**Elemental Mastery:** Choose one element to master:

* Fire (Pyromancer)
* Cold (Cryomancer)
* Lightning (Stormcaller)
* Acid (Venomancer)

Whenever you cast a spell that deals damage of your chosen type, it deals an additional damage die.

**Spell Mastery:** Choose one 1st-level spell. You may cast that spell as a cantrip; it no longer consumes a spell slot.

**Vampiric Conduit:** When you kill a creature using damage of your chosen Elemental Mastery type, there is a 35% + 3% per point of your Luck modifier chance to siphon its essence. You heal for 10% of the elemental damage dealt, up to your maximum hit points.

**Arcane Defiance:** You have a 10% + 1% per point of your Luck modifier chance to completely resist any spell that would affect you, even if you are not the direct target.

**Cataclysm Casting:** Whenever you cast a damaging spell, roll an unmodified d20. On a result of 20, the spell becomes a critical spell and deals double damage dice.

**Spell Reflection:** When a spell directly targets you, there is a 5% + 1% per point of your Luck modifier chance to reflect the spell back at the caster. This does not apply to area-of-effect spells or abilities that do not specifically target you.

\page

Friar

| Level | Title | Feature / Growth Highlights |
| ----- | ----- | --------------------------- |
| 1 | Penitent Wanderer | Spellcasting (Piety), Quarterstaff Mastery |
| 2 | Ashen Disciple | Turn Undead |
| 3 | Flagellant | Uncapped Attribute Growth |
| 4 | Keeper of Relics | Sacred Retribution |
| 5 | Lantern Bearer | Thunderstrike, Empowered Healing |
| 6 | Voice of Penance | Turn Undead (Flee), Sanctified Staff |
| 7 | Mortified Saint | Uncapped Attribute Growth |
| 8 | Warden of Ash | Divine Restoration |
| 9 | Living Reliquary | Embrace of Solace |
| 10 | Saint of the Last Rite | Turn Undead (Annihilation), Uncapped Attribute Growth |

**Spellcasting:** You are a full caster. Your spellcasting ability is Piety.

**Quarterstaff Mastery:** Your preferred weapon is the quarterstaff. While wielding a quarterstaff, your attacks score a critical hit on a roll of 19-20. On a critical hit, the target is stunned until the end of its next turn.

**Turn Undead:** Requires a holy symbol of Solace. As an action, all undead must make a Piety saving throw against your spell DC. On a failure, they gain the Frightened condition and may repeat the save at the end of each of their turns.

This ability may be used once per combat and up to three times before requiring a Rest.

If an undead creature rolls a natural 1 on this saving throw, it is destroyed.

**Uncapped Attribute Growth:** You can permanently increase two attributes by 1 point each, or increase one attribute by 2 points.

**Sacred Retribution:** When an undead creature hits you with a melee attack, you may immediately make a melee attack against that creature, provided it is within your reach and you are wielding a melee weapon. This effect can only occur once per turn.

**Thunderstrike:** When you hit with a melee attack, there is a 15% + 1% per point of your Luck modifier chance that Solace's wrath calls down a bolt of lightning upon your target, dealing an additional 4d6 lightning damage.

**Empowered Healing:** Your healing spells restore an additional die of healing.

**Turn Undead (Flee):** Undead that fail their saving throw now flee. You gain full experience as if they were slain, but they drop no treasure.

**Sanctified Staff:** Your quarterstaff attacks deal an additional die of holy damage.

**Divine Restoration:** Your healing spells can now critically heal. When you cast a healing spell, roll a d20; on a 20, the healing is doubled as per a critical hit.

**Embrace of Solace:** Damage that would reduce you to 0 hit points instead reduces you to 1 hit point. This effect can occur once and recharges after a Rest.

**Turn Undead (Annihilation):** Undead that fail their saving throw are destroyed.

\page

Crusader

| Level | Title              | Feature / Growth Highlights                                 |
| ----- | ------------------ | ----------------------------------------------------------- |
| 1     | Oathbound          | Spellcasting (Piety), Sacred Touch, Aura of Solace          |
| 2     | Iron Zealot        | Fearless Faith, Plague Ward                                 |
| 3     | Faithforged        | Uncapped Attribute Growth                                   |
| 4     | Relic Bearer       | Holy Smite                                                  |
| 5     | Dawnbreaker        | Blinding Judgement, Sacred Touch (2 charges)                |
| 6     | Sanctified Blade   | Exile the Unclean                                           |
| 7     | Martyr Knight      | Uncapped Attribute Growth                                   |
| 8     | Relentless Templar | Bulwark of Faith                                            |
| 9     | Judicator          | Unshaken                                                    |
| 10    | Divine Exemplar    | Purity Incarnate, Cleansing Touch, Sacred Touch (3 charges) |

**Spellcasting:** You are a half caster. Your spellcasting ability is Piety.

**Sacred Touch:** You may touch yourself or an ally to restore health equal to 1d8 per level. This ability recharges after a Rest.

At Level 5, this ability gains 2 charges before requiring a Rest.
At Level 10, this increases to 3 charges.

**Aura of Solace:** Allies adjacent to you gain +1 to saving throws and +1 AC against attacks and spells from evil creatures.

**Fearless Faith:** You have advantage on all effects that would cause the Frightened condition.

**Plague Ward:** You have resistance to all effects that cause disease.

**Uncapped Attribute Growth:** You can permanently increase two attributes by 1 point each, or increase one attribute by 2 points.

**Holy Smite:** Your melee attacks deal an additional damage die as holy damage when striking evil creatures.

**Blinding Judgement:** When you hit an evil creature with a melee attack, it must succeed on a Piety saving throw against your spell DC or be blinded until the end of its next turn.

**Exile the Unclean:** When you strike a fiend or undead with a melee attack, it must succeed on a Piety saving throw against your spell DC or be banished from the plane. Your party gains full experience for defeating enemies this way. Boss-type enemies are immune to this effect.

**Bulwark of Faith:** While you have a shield equipped, attacks against you cannot be critical hits.

**Unshaken:** You are immune to the Frightened condition.

**Purity Incarnate:** You are immune to disease.

**Cleansing Touch:** You may touch an ally to remove all diseases affecting them. This ability recharges after a Rest.

\page

Troubadour

| Level | Title                | Feature / Growth Highlights                                                   |
| ----- | -------------------- | ----------------------------------------------------------------------------- |
| 1     | Wandering Minstrel   | Spellcasting (Personality), Instrumentalist, Gift of Song, Silver Performance |
| 2     | Silver Tongue        | Beguiling Resistance, Songcraft (learn a new Song)                            |
| 3     | Verseweaver          | Uncapped Attribute Growth                                                     |
| 4     | Lute of Lament       | Songcraft (learn a new Song)                                                  |
| 5     | Balladeer of War     | Unshaken Chorus                                                               |
| 6     | Dirge Singer         | Songcraft (learn a new Song)                                                  |
| 7     | Echo-Bound Poet      | Uncapped Attribute Growth                                                     |
| 8     | Harbinger of Refrain | Voice Unbroken                                                                |
| 9     | Voice Unbroken       | Songcraft (learn a new Song)                                                  |
| 10    | Maestro of Ruin      | Endless Aria, Arcane Refrain                                                  |

**Spellcasting:** You are a half caster. Your spellcasting ability is Personality.

**Instrumentalist:** You may use instruments that you find, including those of magical nature.

**Gift of Song:** You can perform Songs to support your party in combat. Starting or maintaining a Song requires a bonus action. Songs do not require an instrument.

A Song lasts for the duration of combat and ends if you are affected by a Silence effect or if you cast a spell. You may still attack while singing.

You may perform a number of Songs equal to 3 + your level before needing to Rest. Resting restores all uses.

At character creation, choose one Song from the Song list.

**Silver Performance:** Your party may stay at inns for free, as you perform in exchange for food and lodging. You must have an instrument in your inventory (mundane or magical) for this ability to function.

**Beguiling Resistance:** You have resistance to spells and effects that attempt to charm, beguile, or otherwise manipulate your mind.

**Songcraft:** You learn an additional Song from the Song list.

**Uncapped Attribute Growth:** You can permanently increase two attributes by 1 point each, or increase one attribute by 2 points.

**Unshaken Chorus:** While you are performing a Song, you are immune to the Frightened condition.

**Voice Unbroken:** Your voice cannot be silenced by magical or mundane means.

**Endless Aria:** You can now cast spells without ending your Song.

**Arcane Refrain:** While performing a Song, there is a 5% + 1% per point of your Luck modifier chance that any spell you cast does not consume a spell slot.

**Song Persistence:** All buffs and debuffs from Troubadour songs are active only as long as the Troubadour continues singing. The Troubadour does not benefit from these effects.

| Song Name | Effect |
| -- | -- |
| March of Iron Vows | All allies gain +1 AC. There is a 1% chance per point of your Luck modifier that this bonus becomes +2 AC. |
| Hymn of the Unbroken | All allies gain +1 to all saving throws. There is a 1% chance per point of your Luck modifier that this bonus becomes +2 to all saving throws. |
| Warcaller’s Crescendo | All allies reroll all 1s on all damage dice and must use the new result. This applies to all sources of damage, including attacks, spells, and abilities. |
| Dirge of Withering | All enemies suffer -1 to hit with all attacks. There is a 1% chance per point of your Luck modifier that this penalty becomes -2 to hit. |
| Ballad of Ruin | All enemies take -1 to all saving throws. There is a 1% chance per point of your Luck modifier that this penalty becomes -2 to all saving throws. |
| Refrain of Mending | At the start of your turn, all allies heal 1d4 HP (cannot exceed maximum hit points). |
| Purging Chorus | At the start of your turn, all allies have a 5% + 1% chance per point of your Luck modifier per condition to remove each negative condition affecting them (each condition is rolled separately). |
| Echoes of Fury | All allies have a 5% + 1% chance per point of your Luck modifier to make an additional attack when they take the Attack action. |

\page








##### Spells


Spellcasters are either full casters or half casters, as in 5E, but with two major differences: there are **no spell slots**—only spells—and the number of spells that can be cast per long rest is doubled.


::



##### Full Caster Spells by Level (Friar, Hedge Wizard) 

| Wizard Level | 1st | 2nd | 3rd | 4th | 5th |
| ------------ | --- | --- | --- | --- | --- |
| 1            | 4   | —   | —   | —   | —   |
| 2            | 6   | —   | —   | —   | —   |
| 3            | 8   | 4   | —   | —   | —   |
| 4            | 8   | 6   | —   | —   | —   |
| 5            | 8   | 6   | 4   | —   | —   |
| 6            | 8   | 6   | 6   | —   | —   |
| 7            | 8   | 6   | 6   | 2   | —   |
| 8            | 8   | 6   | 6   | 4   | —   |
| 9            | 8   | 6   | 6   | 6   | 2   |
| 10           | 8   | 6   | 6   | 6   | 4   |



::




##### Half Caster Spells by Level (Crusader, Warden, Troubadour)

| Ranger Level | 1st | 2nd | 3rd |
| ------------ | --- | --- | --- |
| 1            | 2   | —   | —   |
| 2            | 4   | —   | —   |
| 3            | 6   | —   | —   |
| 4            | 6   | —   | —   |
| 5            | 8   | 4   | —   |
| 6            | 8   | 4   | —   |
| 7            | 8   | 6   | —   |
| 8            | 8   | 6   | —   |
| 9            | 8   | 6   | 4   |
| 10           | 8   | 6   | 4   |



\page




##### Spells




## **Umberhold Caster Summary**

| Class | Abbr. | Stat | Role |
| :--- | :--- | :--- | :--- |
| **Hedge Wizard** | **HW** | **Intellect** | Full Caster |
| **Friar** | **F** | **Piety** | Full Caster) |
| **Troubadour** | **T** | **Personality** | Half Caster |
| **Crusader** | **C** | **Piety** | Half Caster |
| **Warden** | **W** | **Piety** | Half Caster |

---

### **Core Magic Mechanics**

* **Spell Save DC:** $$8 + \text{Proficiency Bonus} + \text{Casting Modifier}$$
* **Cantrips:** Unlimited use; no spell slots required.
* **Buff Icons:** Active spell effects display as icons below the mini-map.

---

### **Updated Master AI Prompt Fragment**

> **Magic System:** Use 5E slot progression. Full Casters (HW, F) vs. Half Casters (C, W). All spells use DC $8 + \text{PROF} + \text{MOD}$. Display "Active Status Icons" under the UI Mini-Map for duration-based spells. Cantrips are free.



\page




{{wide

##### Spells

| Name              | Classes  | Level   | Range | Target                                                     | Duration        | Effect                                                                                                                                                                                 |
| ----------------- | -------- | ------- | ----- | ---------------------------------------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Light             | HW, T    | 1st     | Party | Party                                                      | Until dispelled | Provides 3 squares of illumination in darkness. **ICON: BURNING SUN**                                                                                                                      |
| Mocking Words     | T        | Cantrip | 3     | One enemy                                                  | Instant         | WIS save or take 1d8 psychic damage and suffer disadvantage on the next attack.                                                                                                        |
| Cure Light Wounds | F, W, C  | 1st     | 1     | One ally                                                   | Instant         | Heals 1d8 + Casting Bonus hit points.                                                                                                                                                  |
| Feather Fall      | HW       | 1st     | Party | Party                                                      | Until dispelled         | Immune to falling damage. **ICON: FEATHER**                                                                                                                                                |
| Beguile           | HW       | 1st     | 3     | One enemy                                                  | 1 round/level   | WIS save or become Charmed. The charmed creature does not attack the party. Effect ends if it takes damage from the party. Target may repeat the save at the end of each of its turns to end the effect. |
| Sure Strike       | HW       | 1st     | Party | Party                                                       | 1 turn/level    | Party gains +2 to melee and ranged attacks. **ICON: BLUE GLOWING SWORD**                                                                                                                                |
| Witchlight        | HW, T, W | 1st     | 3     | One enemy                                                  | 1 round/level   | WIS save or target’s AC is reduced by 4. Target may repeat the save at the end of each of its turns to end the effect.                                                                                   |
| Sleep             | HW       | 1st     | 3     | One enemy and up to one each side in the same rank (3 max) | 1 turn/level    | WIS save or fall asleep. Target may repeat the save at the end of each of its turns to end the effect. Effect ends immediately if damage is taken.                                                       |
| Identify | HW      | 1st   | NA    | One item in the caster's inventory | Instant  | Reveals magical properties of the chosen item. |
Shockwave | HW | 1st | 2 | One enemy and one either side | Instant | Sends a shockwave that deals 2d4 bludgeoning damage.
Arcbolt | HW | 1st | 3 | One enemy | Instant | Deals 3d4 lightning damage. Target makes a DEX save for half damage.
Blind | HW | 1st | 2 | One enemy | 1 round/level | WIS save or blinded. Target may repeat the save at the end of each of its turns to end the effect.
Warden's Mark | W | 1st | 3 | One enemy | Combat | Target is marked. The warden attacks the target at +4 to hit and deals an extra die of damage per hit.









}}
