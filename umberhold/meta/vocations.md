# Vocations Meta

Canon source: `umberhold/CURRENT.md`.

## Canon Summary
- Umberhold defines **12 vocations**.
- A vocation is chosen at character creation.
- It grants a passive **Boon** that is always active and cannot be changed.
- Each vocation has a **player-facing description** and a **hidden mechanical effect**.
- Players are not shown the exact mechanics at character creation.

## Canon Vocations

| Vocation | Player-Facing Boon | Hidden Mechanics |
|---|---|---|
| Whipping Boy / Girl | You have learned to endure punishment that would break others. | When you are hit by a critical hit, roll a d3. On a 1, the hit becomes a normal hit instead. |
| Poison Taster | Your body has grown accustomed to toxins. | Advantage on saves against poison. Poison damage taken is reduced by 25% (rounded down). |
| Gong Farmer | Foul air does not affect you as it once did. | You cannot gain the Poisoned condition from gases. |
| Sin Eater | Unseen forces do not always take hold of you. | When targeted by a spell that requires a saving throw, roll a d10. On a 1, the spell has no effect on you. |
| Leech Collector | Your body no longer fears the loss of blood. | You are immune to bleeding effects. |
| Rat Catcher | You are quicker than most, especially in tight spaces. | You gain +1 Agility. |
| Mudlark | You rarely miss what others overlook. | You have Advantage on all Perception checks. |
| Plague Burier | Disease has lost its hold on you. | You are immune to disease. |
| Knacker | You know how to strike to do real harm. | You deal +1 damage to all melee attacks. |
| Toad-Eater | You can endure toxins that would sicken others. | Advantage on saves against poison. Poison damage taken is reduced by 25% (rounded down). |
| Chimney Sweep | You move easily through tight and dangerous spaces. | You gain +4 to Agility saving throws. |
| Gibbet-Cleaner | You are difficult to unsettle, even in the face of horror. | You have Advantage on saves against Fear effects. |

## Implementation Notes
- Vocations are passive background perks.
- Boons are always on and do not change after character creation.
- The hidden-mechanics model means the character creator should surface flavor, not exact rules text.
- `umberhold/list.md` already establishes no vocation-specific dialogue or quest branching in the vertical slice.
