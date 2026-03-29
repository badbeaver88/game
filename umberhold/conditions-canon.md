# Umberhold Conditions Canon

This document captures the current approved condition list for Umberhold.

These conditions may still be tuned later, but this file records the current working canon.

It does **not** modify `MASTER.md`.

---

## 1. Condition List

### Beguiled
The target is confused, takes no hostile actions, and does not move.

Rules:
- the target does not take hostile actions
- the target does not move
- the condition ends immediately if the target takes damage

---

### Bleeding
The target is suffering a damage-over-time wound.

Rules:
- **Bleeding** is a damage-over-time effect
- the source that applied **Bleeding** defines the damage amount
- the source that applied **Bleeding** also defines the damage type, if relevant
- unless a source says otherwise, the damage is taken at the **start of the target's next turn**
- after that damage resolves, **Bleeding** ends unless the source says it lasts longer

---

### Blinded
The target cannot see.

Rules:
- attacks against the target have **advantage**
- attacks made by the target have **disadvantage**

---

### Burning
The target is on fire and suffers damage over time.

Rules:
- **Burning** is a damage-over-time effect
- the source that applied **Burning** defines the damage amount
- **Burning** damage is normally **fire** damage unless a source explicitly says otherwise
- unless a source says otherwise, the damage is taken at the **start of the target's next turn**
- after that damage resolves, **Burning** ends unless the source says it lasts longer

---

### Frightened
The target is overcome by fear.

Rules:
- the target has **disadvantage** on attacks
- the target cannot willingly move forward on the combat grid

---

### Paralyzed
The target is physically locked in place.

Rules:
- the target cannot take actions
- the target cannot move
- attacks against the target have **advantage**
- melee attacks against the target are automatic **critical hits**
- the target automatically fails **Strength** and **Agility** saving throws

---

### Poisoned
The target is suffering from poison.

Rules:
- the target has **disadvantage** on attacks
- the target has **disadvantage** on ability checks

---

### Silenced
The target cannot produce speech-based magical effects.

Rules:
- the target cannot cast spells that require speech
- the target cannot use abilities that require speech
- this includes songs and similar vocal performances

---

### Slept
The target is in unnatural sleep.

Rules:
- the target cannot take actions
- the target cannot move
- attacks against the target have **advantage**
- melee attacks against the target are automatic **critical hits**
- the target automatically fails **Strength** and **Agility** saving throws
- the target wakes immediately if it takes damage

---

### Stunned
The target is dazed and unable to act normally.

Rules:
- attacks against the target have **advantage**
- the target has **disadvantage** on attacks
- the target has **disadvantage** on **Strength** and **Agility** saving throws

---

## 2. Current Condition Summary

The current approved condition list is:
- Beguiled
- Bleeding
- Blinded
- Burning
- Frightened
- Paralyzed
- Poisoned
- Silenced
- Slept
- Stunned

---

## 3. Notes on Current Canon

These conditions are currently captured as approved working rules.

Three implementation notes remain worth reviewing later:
- Umberhold currently does **not** use reactions, so any reaction-denial text is unnecessary under current canon.
- Player characters do not normally move during combat, so movement-restriction conditions may matter primarily for enemies unless later mechanics expand party movement.
- **Burning** and **Bleeding** are source-defined damage-over-time conditions, with the current default pattern being damage at the start of the target's next turn.

These are not blockers, but they are useful for future cleanup.

---

## 4. Still Open for Later Canonization

The following are still open and may need later clarification:
- whether Beguiled and Soothed should be separate conditions or the same rules concept
- whether Stunned should also prevent main actions entirely
- whether Frightened affects spell targeting or only attacks
- whether Blinded affects spellcasting for targeted spells
- whether multiple **Burning** or **Bleeding** applications stack, refresh, or overwrite one another
- whether condition durations always expire at start or end of turn depending on source
- whether bosses can be immune to some control conditions by default
- whether there are cleanse rules tied to items, spells, or rest

---

## 5. Implementation Note

This file is a standalone approved rules sheet.
It does **not** modify `MASTER.md`.
