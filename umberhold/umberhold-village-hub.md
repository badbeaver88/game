# Umberhold Village Hub

> Naming note: use **Gravenhold Manor** as the current name for the manor. Older project notes that say **Gravenhollow Manor** should be treated as legacy wording to clean up later.

This file is the clean implementation-ready spec for the **Umberhold** opening hub, its quests, its UI-facing journal behavior, and its reactive NPC state changes.

---

## 1. Design Intent

Umberhold is the opening **hub village** and the party's first reliable refuge.

It is meant to feel:
- fearful
- decaying
- suspicious
- barely functional
- safer than the wilds, but not truly safe

### Core structure
- **Intended first main path:** Gravenhold Manor
- **Optional, deadlier side content:** Graveyard and Well/Trolls
- **Sandbox rule:** players may attempt dangerous content early and die
- **Failure rule:** a TPK is acceptable; players reload at the inn and return later with better levels, spells, and gear

### Difficulty signposting
The game should **warn**, not forbid.

NPCs, rumors, and environmental details should make the risk readable:
- **Gravenhold Manor** = dangerous, but the clearest first move
- **Graveyard** = more dangerous than it first appears
- **Well/Trolls** = highly lethal if attempted too early

---

## 2. Village Overview

Umberhold is a small, rotting medieval village hemmed in by mud, fear, and bad omens.

Mud-choked roads wind between leaning cottages with sagging roofs. Gardens have gone to ruin under thorn and rot. Doors are barred. Windows are shuttered. Smoke rises from only a handful of chimneys.

Few villagers linger outside. Those who do speak in hushed tones and break off conversation the moment the party approaches. Nearly all nervous glances drift northwest toward **Gravenhold Manor**.

At night, noises carry from that direction:
- scraping
- distant howls
- thin laughter on the wind

The village is ringed by a crude wooden palisade. The **South Gates** remain shut. Villagers whisper that the roads beyond are watched by things that do not openly attack, but stalk and drive travelers back.

---

## 3. Journal UI

The party has a **Journal** tracked through a **book icon on the UI**.

### Player-facing purpose
The Journal exists to let the player quickly review:
- quest title
- complete / incomplete state
- who gave the quest or how it was learned
- a short summary of the NPC's concern or the quest outline
- current objectives
- completion summary once resolved

### UI rules
- The Journal book icon is visible in:
  - village hub screens
  - exploration HUD
- The Journal is **read-only** while open
- The Journal should not interrupt combat flow; in combat it may be hidden or disabled
- Journal state is saved with the current save file
- Reloading restores Journal state from the last inn save

### Journal layout
Each entry should show:
1. **Title**
2. **Status:** Incomplete or Complete
3. **Source:** NPC name or interaction source
4. **Source Summary:** brief summary of what the NPC said or what the party observed
5. **Quest Summary:** current narrative framing
6. **Objectives:** checklist-style items
7. **Completion Note:** only shown when complete

### Journal update triggers
Update the Journal when:
- the party inspects key props
- a quest-giver gives new information
- a dungeon entrance is found
- a boss or scripted threat is defeated
- a quest is turned in

### Journal and Quest Items
The Journal is separate from the existing **Quest Items** tab.
- **Journal** = information
- **Quest Items** = permanent key items required for progression

---

## 4. Locations

## 4.1 Umberhold Inn

**NPC:** Bartholomew  
**Role:** Innkeeper / safe management hub

### Services
| Option | Effect |
|---|---|
| Rest | 25 gp; free if Troubadour in party; 8 hours; functions as Long Rest |
| Rest Until Dawn | Pass time without restoring resources |
| Create Character | Opens character creation |
| Delete Character | Removes character |
| Add Character to Party | Adds character to active party |
| Remove Character from Party | Removes character from active party |
| Save Game | Save progress |
| Load Game | Load progress |
| Listen for Gossip | Roll on village gossip table |

### Dialogue
**Greeting**  
> “Keep your voice low… walls carry sound these days. You here to stay, or just passing through… if passing through’s still a thing?”

**Rest**  
> “You’ll sleep safer here than most places… though I won’t promise you’ll sleep easy.”

**About the village**  
> “Used to be folk laughed here. Now they listen. Always listening.”

**About the manor**  
> “No one sane goes there by choice. Which means you’re either brave, desperate… or not from here.”

### Gossip Table (d6)
| Roll | Gossip |
|---|---|
| 1 | “Lights in the manor windows… but no one’s lived there in years.” |
| 2 | “Old Etheldreda—gone. Just gone. Door locked, note nailed. Not right.” |
| 3 | “Graveyard’s not quiet anymore… heard scratching under the soil.” |
| 4 | “Wymarc says stay calm. Easy for him—he don’t leave his desk.” |
| 5 | “Something’s been stealing livestock… not wolves. Too clever.” |
| 6 | “A child swears he saw small shapes near the manor… crawling.” |

---

## 4.2 Iron Shovel & Scutage

**NPC:** Oswaldine  
**Role:** Merchant / identifier / weapon silvering

### Services
| Option | Details |
|---|---|
| Buy | Mundane weapons, armor, gear |
| Sell | 50% value |
| Identify | 125 gp per item |
| Silver One-Handed Melee Weapon | 50 gp |
| Silver Two-Handed Melee Weapon | 100 gp |

Oswaldine does **not** sell pre-silvered weapons. She only silvers melee weapons the party already owns.

### Identification rules
| Item Tier | Chance Unidentified |
|---|---|
| Lesser | 25% |
| Greater | 50% |
| Exalted | 80% |

### Dialogue
**Greeting**  
> “Gold talks. If you’ve got it, I’ve got something worth your trouble.”

**Identify**  
> “Magic’s tricky. You want to know what you’re holding, you pay for the knowing.”

**Silver weapons**  
> “I don’t sell silvered blades. Bring me your weapon, bring me the silvering fee, and I’ll do the work proper.”

**About the well**  
> “If you’re going down that shaft, buy oil. And if you’re clever, fire.”

**About the graveyard**  
> “Dead things don’t stay buried east of here. Not lately.”

**About the manor**  
> “Manor’s cursed, haunted, infested, or all three. Bring rope.”

---

## 4.3 Solcine Chantry

**NPC:** Acolyte Gidney  
**Role:** Healing / resurrection / anti-curse services

### Services
| Item/Service | Cost |
|---|---|
| Holy Water | Standard |
| Silver Holy Symbol | Standard |
| Cure Poison | 100 gp |
| Cure Disease | 100 gp |
| Remove Curse | 100 gp |
| Resurrection | 500 gp × character level; uses resurrection failure formula |

### Dialogue
**Greeting**  
> “Solace watches, even here… though her light feels distant.”

**About the village**  
> “Something festers beneath this place. I feel it in my prayers.”

**About the graveyard**  
> “The earth there is troubled. The dead are not at rest.”

**About the manor**  
> “There is corruption there, yes—but also purpose. Something is being done, not merely haunting.”

---

## 4.4 Alchemist’s Mortar

**NPC:** Etheldreda  
**State at game start:** Missing

A crooked shop with faded signage:

> **Etheldreda’s Potions**

A crude note is nailed to the door:

> “Shop closed.”  
> — Bailiff Wymarc

The door is locked.

### Interaction options
- Inspect Door
- Examine Note
- Try Handle
- Leave

### Environmental clues
- dust on the step, but scrape marks near the threshold
- note nailed in crookedly and hurriedly
- lock recently handled
- the wording is abrupt and feels unlike a proper civic notice

### Trigger
Inspecting the shop adds **The Missing Alchemist** to the Journal.

### Post-rescue state
After Etheldreda is rescued from beneath Gravenhold Manor, the shop can reopen.

### Reopened service role
Etheldreda becomes Umberhold's potion and alchemy vendor.
Exact potion inventory can be finalized later, but the shop should support:
- buying potions
- buying alchemical curatives
- future ingredient or utility hooks if desired

---

## 4.5 The Bailiff’s Desk

**NPC:** Wymarc  
**Role:** Primary quest dispatcher

Wymarc is stout, anxious, and overworked. He is not secretly evil, but he is visibly withholding and trying to manage panic with incomplete information.

### Suspicious detail
Whenever Etheldreda is mentioned, Wymarc becomes tense, avoids eye contact, and fidgets with a folded scrap of parchment. Players should briefly wonder if he is involved.

### Truth
He is hiding fear and uncertainty, not guilt. He suspects the manor is involved, but lacks proof and fears open panic.

### Greeting
> “Ah—new faces. Good. Means you’ve not been scared off yet… or eaten.”

### Critical signposting line
> “Manor’s the heart of it, I think. Graveyard’s uglier. Well’s deadlier. If I were you, I’d choose my battles careful.”

That line should be preserved. It is the clearest in-world warning that the side threats may be deadlier than the manor.

---

## 4.6 Village Well

**Quest tie:** Troll Trouble  
**Content type:** Set-piece descent + immediate combat  
**Not a dungeon**

This is **not** a separate exploration dungeon.

### Surface presentation
The village well sits under nervous watch. A rope and bucket rig are already present.
Villagers avoid getting close.

### Interaction flow
1. Party inspects the well
2. If they choose to descend, they use the existing rope and bucket setup
3. On descent, they encounter the trolls below
4. The game switches directly to the **combat grid**
5. There is no dungeon floor to explore
6. Once the trolls are slain, the party simply climbs back up

### Design purpose
This should feel like a fast, brutal, high-risk set piece:
- immediate danger
- no mapping reward
- no navigation puzzle
- pure combat challenge tied to village survival

### Danger signposting
Before descent, communicate risk through:
- foul wet stench rising from below
- gnawed livestock bones near the stone lip
- strained villagers refusing to approach
- Oswaldine's fire warning
- Wymarc's “Well’s deadlier” line

---

## 4.7 East Graveyard

**Quest tie:** The Restless Dead  
**Content type:** Small single-level dungeon

### Surface presentation
The graveyard lies east of the village. Graves are disturbed. Soil is sunken in places. Candles have long since gone out.

At the rear of a mausoleum stands a **dark stair** descending below ground.

### Dungeon structure
- uses the same **26 × 26 grid** as the rest of the game
- only **one level**
- entered through the mausoleum stair
- themed as a compact, deadlier-than-expected side dungeon

### Intended feel
The graveyard should present as solemn and eerie on the surface, then become a claustrophobic necrotic undercroft below.

### Danger signposting
Use:
- scratching sounds beneath the soil
- Acolyte Gidney's warnings
- cold air from the mausoleum stair
- signs of forced or repeated burial disturbance

---

## 4.8 South Gates

**NPC:** Warden Halvric  
**Role:** Progression lock

### Dialogue
**Greeting**  
> “Not safe beyond the walls. Not anymore.”

**Ask to leave**  
> “Orders are clear—I don’t open these gates without Wymarc’s say.”

**Press further**  
> “Road south looks open, if you don’t know better. But folk who try it come back wild-eyed—or don’t come back at all.”

### System rule
The party cannot leave Umberhold until the **Boggart Boss beneath Gravenhold Manor** is defeated.

### In-world reinforcement
The road is not merely closed by authority. It is believed to be watched by hostile unknowns that stalk travelers and drive them back.

---

## 5. Quests

## 5.1 The Missing Alchemist

**Type:** Main quest  
**Intended first major objective:** Yes

### Acquisition
- inspect Alchemist’s Mortar
- speak with Wymarc

### Source summary
Wymarc believes Etheldreda did not leave willingly and suspects disappearances near the manor are connected.

### Objectives
- Investigate Gravenhold Manor
- Search for Etheldreda
- Descend beneath the manor
- Rescue Etheldreda
- Defeat the Boggart Boss

### Hidden truth
Etheldreda is held beneath the manor and forced to brew strengthening potions for the Boggart Boss.

### Reward
- 1,000 gp
- 3 rolls on Lesser Magical Items table
- 1 roll on Greater Magical Items table

### Village consequence
- Etheldreda returns
- Alchemist’s Mortar can reopen
- more villagers appear outdoors
- hopeful gossip variants unlock
- South Gate progression advances

### Journal text
**Incomplete summary**  
Etheldreda, Umberhold’s alchemist, has vanished. Her locked shop and Wymarc’s tense explanation suggest she was taken, not gone willingly. The manor to the northwest is the likeliest place to begin.

**Complete summary**  
Etheldreda was held beneath Gravenhold Manor and forced to brew for the creature ruling the depths. She has been rescued, and Wymarc owes the party a reward.

---

## 5.2 The Restless Dead

**Type:** Side quest  
**Danger:** High  
**Available early:** Yes  
**Ideal after manor:** Yes

### Acquisition
- speak with Wymarc
- hear graveyard gossip
- speak with Gidney

### Source summary
Wymarc says villagers can no longer mourn safely because something in the graveyard is waking the dead.

### Objectives
- Investigate the graveyard
- Enter the mausoleum
- Descend the dark stair
- Destroy the undead presence
- Stabilize or consecrate the site

### Reward
- 500 gp
- 2 Lesser Magical Item rolls

### Village consequence
- funeral rites resume
- villagers place flowers and candles again
- Gidney gains relieved dialogue
- east side village ambience becomes less fearful

### Journal text
**Incomplete summary**  
Something has disturbed the graveyard east of Umberhold. The dead no longer rest quietly, and a dark stair in the rear mausoleum appears to lead to the source below.

**Complete summary**  
The corruption beneath Umberhold’s graveyard has been broken. The dead can be mourned again, and the chantry’s rites no longer feel futile.

---

## 5.3 Troll Trouble

**Type:** Side quest  
**Danger:** Very High  
**Available early:** Yes  
**Ideal after manor:** Yes

### Acquisition
- speak with Wymarc
- hear rumors around the well
- ask Oswaldine about the well

### Source summary
The village water source is controlled by trolls below the well, and the villagers have been paying tribute in livestock to avoid worse losses.

### Objectives
- Inspect the well
- Descend using the rope and bucket rig
- Kill the trolls
- Climb back out and secure the water source

### Reward
- 500 gp
- 2 Lesser Magical Item rolls

### Village consequence
- clean water returns
- villagers gather near the well again
- ambient fear drops slightly
- inn prices may optionally fall
- Oswaldine comments on trade improving

### Journal text
**Incomplete summary**  
Trolls have taken the village well and the water below it. There is no dungeon to explore here—only a rope descent into immediate danger. If the party goes down, they should be ready to fight at once.

**Complete summary**  
The trolls below the well are dead. Umberhold’s water is safe again, and villagers can finally gather at the well without fear.

---

## 6. NPC Dialogue Trees

## 6.1 Bartholomew
- Greeting
- Rest
- Rest Until Dawn
- Ask about village
- Ask about manor
- Ask about Wymarc
- Ask about Etheldreda
- Listen for gossip

## 6.2 Oswaldine
- Greeting
- Buy
- Sell
- Identify
- Silver one-handed melee weapon
- Silver two-handed melee weapon
- Ask about village
- Ask about well
- Ask about graveyard
- Ask about manor

## 6.3 Acolyte Gidney
- Greeting
- Ask about village
- Buy holy water
- Cure poison
- Cure disease
- Remove curse
- Resurrection
- Ask about graveyard
- Ask about manor
- Ask about Etheldreda

## 6.4 Wymarc
- Greeting
- Who are you?
- What’s wrong with this village?
- Ask about Etheldreda
- Ask about the graveyard
- Ask about the well
- Ask which threat is worst
- Ask about the gates

## 6.5 Warden Halvric
- Greeting
- Ask to leave
- Press further
- Ask what’s out there
- Post-manor unlock line

## 6.6 Etheldreda (post-rescue)
- Greeting
- Thank the party
- Buy potions
- Ask what happened beneath the manor
- Ask about Wymarc’s closure note
- Ask about the village now

---

## 7. Post-Quest Reactivity Rules

NPCs should react after each quest resolves.

### After The Missing Alchemist
- Etheldreda returns and reopens later
- Bartholomew sounds slightly relieved
- Wymarc becomes less guarded
- Halvric loosens from pure refusal into exhausted approval once gate progression unlocks
- Gidney frames the victory as only a partial cleansing

### After The Restless Dead
- Gidney becomes visibly lighter in tone
- villagers return to graves with offerings
- Bartholomew's gossip loses one of its graveyard dread lines
- Wymarc acknowledges the village can mourn again

### After Troll Trouble
- villagers gather near the well
- Oswaldine comments on improved supply and trade
- Bartholomew may optionally lower lodging cost
- Wymarc sounds more practical than desperate

### After all three
Umberhold should feel changed, but not fully healed. It becomes a place with surviving hope, not total safety.

---

## 8. Journal Entry Templates

These are the player-facing text blocks.

### Quest Added: The Missing Alchemist
Etheldreda, Umberhold’s alchemist, has vanished. Her shop is locked, and a crude note signed by Bailiff Wymarc claims it is closed. Something about the place feels wrong.

### Updated: The Missing Alchemist
Wymarc believes Etheldreda did not leave willingly. Several disappearances have occurred near Gravenhold Manor, and he suspects she was taken there.

### Completed: The Missing Alchemist
Etheldreda was being held beneath Gravenhold Manor and forced to brew for the thing ruling the depths. She has been rescued.

### Quest Added: The Restless Dead
Something is wrong with the graveyard east of Umberhold. The dead are said to scratch beneath the earth, and a dark stair in the rear mausoleum may lead to the source.

### Updated: The Restless Dead
The unrest beneath the graveyard has a source. If the village is to know peace, it must be destroyed below the mausoleum.

### Completed: The Restless Dead
The dead beneath Umberhold’s graveyard have been put down and the site has been stabilized. Villagers may mourn properly again.

### Quest Added: Troll Trouble
Trolls have taken the village well and the water below it. A rope and bucket rig already hangs there; if the party descends, they will face immediate danger.

### Updated: Troll Trouble
There is no maze below the well—only a direct fight for the village’s water. If the trolls are not slain, Umberhold remains under tribute.

### Completed: Troll Trouble
The trolls below the well are dead. The village water is safe again.

---

## 9. Implementation Notes

### State flags
Recommended village flags:
- `q_missing_alchemist_started`
- `q_missing_alchemist_complete`
- `q_restless_dead_started`
- `q_restless_dead_complete`
- `q_troll_trouble_started`
- `q_troll_trouble_complete`
- `etheldreda_rescued`
- `alchemist_shop_reopened`
- `south_gate_unlocked`
- `graveyard_stabilized`
- `well_secured`

### Content authoring model
- **Village** uses dialogue nodes, service menus, and set-piece interactions
- **Well** uses a direct interaction-to-combat handoff
- **Graveyard** uses a single-level 26 × 26 authored dungeon
- **Manor** remains the first full main dungeon

### Save/load expectations
The Journal, quest flags, village state changes, and unlocked services must be included in inn saves.

---

## 10. Player-Facing Handout

### Umberhold
Umberhold is a village in slow collapse.

Its roads are mud, its cottages lean, and few windows ever open. The villagers are afraid of the manor to the northwest, the graveyard to the east, and the well at the village center. Even the gates to the south remain shut.

### First impressions
- villagers avoid eye contact
- doors stay barred
- guards keep the south gate closed
- rumors spread faster than facts
- fear feels routine here

### Important places
- **Umberhold Inn** — rest, save, party management, gossip
- **Iron Shovel & Scutage** — buy, sell, identify
- **Solcine Chantry** — healing, holy goods, resurrection
- **Alchemist’s Mortar** — locked at first; owner missing
- **The Bailiff’s Desk** — local authority and quest direction
- **Village Well** — presently dangerous
- **East Graveyard** — visibly disturbed

### Important people
- **Bartholomew**, innkeeper
- **Oswaldine**, merchant
- **Acolyte Gidney**, chantry keeper
- **Wymarc**, bailiff
- **Warden Halvric**, gate guard
- **Etheldreda**, missing alchemist

### Current threats
- **Gravenhold Manor** — the likeliest source of the village’s troubles
- **The Graveyard** — the dead do not rest there
- **The Well** — trolls have seized the water below

### GM note
Players may pursue these in any order. The world should strongly hint that the manor is the intended first move, while the graveyard and well are more deadly than they look.
