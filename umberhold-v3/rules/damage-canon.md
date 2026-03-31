# Umberhold Damage Canon

This document captures the current approved rules for:
- damage types
- vulnerability, resistance, and immunity
- critical hits
- natural 1 attack rolls
- death at 0 or fewer hit points

It is written as a standalone canon reference and does not modify any master reference file.

---

## 1. Damage Types

The current damage types in Umberhold are:

- Slashing
- Piercing
- Bludgeoning
- Fire
- Cold
- Lightning
- Poison
- Acid
- Holy
- Unholy
- Arcane
- Shock
- Falling
- Psychic

---

## 2. Damage Modifiers

### Vulnerability
If a target is vulnerable to a damage type:
- it takes **double damage** from that damage type

### Resistance
If a target is resistant to a damage type:
- it takes **half damage** from that damage type
- always **round down**
- resistance damage can never go below **1 damage** if the attack would otherwise deal damage

### Immunity
If a target is immune to a damage type:
- it takes **no damage** from that damage type

---

## 3. Critical Hits

A critical hit occurs when an attack roll is a **natural 20**.

### Critical Hit Rules
- the natural 20 is checked **before modifiers**
- some features may expand the critical range
- if a feature expands the critical range, it will explicitly say so
- example expanded range: **19-20**

### Critical Damage Rule
On a critical hit:
- **roll all damage dice twice**
- then add any flat bonuses or modifiers

Example:
- Normal hit: `1d8 + 3`
- Critical hit: `2d8 + 3`

---

## 4. Natural 1 Rule

A **natural 1** on an attack roll is always a miss.

This is true regardless of modifiers.

---

## 5. Death Rule

Umberhold does **not** use death saves.

If a character is reduced to **0 or fewer hit points**, they die immediately.

### Immediate Death Rules
- there is no unconscious state
- there is no stabilization state
- there are no recovery rolls
- death happens immediately when current hit points reach `0` or below

### Example
A character with `5 / 40` hit points takes `10` damage.
Their hit points fall below `0`.
They die immediately.

---

## 6. Approved Rules Captured Here

This document locks in the following:
- the current list of Umberhold damage types
- vulnerability = double damage
- resistance = half damage, round down, minimum 1 damage
- immunity = no damage
- critical hit on natural 20 by default
- some features may expand critical range
- critical hits roll damage dice twice, then add bonuses
- natural 1 always misses
- death saves are not used
- 0 or fewer hit points means immediate death

---

## 7. Still Open for Later Canonization

The following are still open and should be resolved elsewhere if needed:
- interaction order between critical hits and vulnerability/resistance
- whether mixed-damage attacks split damage by type before applying modifiers
- whether damage-over-time effects can critically hit
- whether environmental damage uses the same resistance rules in all cases
- whether Holy / Unholy / Arcane / Shock have special systemic interactions beyond type tags
- whether monsters follow the exact same death rule presentation as player characters

---

## 8. Implementation Note

This file is a standalone approved rules sheet.
It does **not** modify `DESIGN.md`.
