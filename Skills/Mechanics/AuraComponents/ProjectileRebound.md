## Description
Applies an [aura](/Skills/Mechanics/Aura) that rebounds incoming projectiles away from the aura holder, optionally sending them back at whoever fired them.

## Attributes
| Attribute | Aliases | Description | Default |
|-----------|---------|-------------|---------|
| onReboundSkill | onrebound, orb, onreflect, ondeflect | Skill executed each time a projectile is rebounded | |
| returnMode | mode | How the rebounded projectile is aimed: `ORIGINAL_CASTER` sends it back toward whoever fired it, `MIRROR` reflects it like a mirror | ORIGINAL_CASTER |
| reparseFaction | reparse, rf, changeshooter, cs | Reassigns the rebounded projectile's shooter to the aura holder, so faction and targeting are re-evaluated | true |
| cancelIncoming | cancelhit, cancel, cancelevent, ce | Cancels the original incoming projectile hit | true |
| vanillaProjectiles | vanilla, vp | Whether vanilla projectiles are rebounded | true |
| mythicProjectiles | mythic, mp | Whether Mythic projectiles are rebounded | true |
| speedFactor | speed, sf | Multiplier applied to the rebounded projectile's speed | 1.0 |
| powerFactor | power, pf | Multiplier applied to the rebounded projectile's power | 1.0 |
| reboundDistance | distance, offset, push | Distance from the holder at which the rebounded projectile is spawned | 0.6 |
| maxRebounds | max, mr | Maximum number of times a single projectile can be rebounded | 1 |
| reboundConditions | conditions, cond, c | [Conditions](/Skills/Conditions) evaluated before a projectile is rebounded | |

## Aliases:
- [x] projectilereflect
- [x] reboundprojectiles
- [x] reboundingprojectiles
