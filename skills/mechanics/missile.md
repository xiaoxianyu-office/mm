## Description
The missile skill is similar to the projectile skill. Missiles however
are homing and will track down their targets. The available syntax is
very similar to that of the projectile skill, too, but has some distinct
differences. **Missiles cannot be summoned as the "METEOR"-type and cannot
hug the surface**.  
However you can edit the inertia, add an onStart-skill and specify wether or not the missiles can only hit their targets.  
Missiles can target both a location and an entity.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| Inertia   | in        | Sets the "turning-rate" of the missile. Lower values make the missile turn around faster. Use big numbers (10-100) when trying to make your missiles turn slowly.         | 1.5     |
| onStart   | oS        | Meta-Skill executed when the projectile starts                       |         |
| onTick    | oT        |Meta-Skill executed every \[interval\] ticks at the projectile's origin location|
| onEnd     | oE        | Meta-Skill executed when the projectile ends                         |         |
| onHit     | oH        | Meta-Skill executed when the projectile hits something. Targets hit are inherited by the meta-skill                                                                    |         |
| Interval  | int, i    | How often (in ticks) the projectile update                           | 4       |
| HorizontalRadius | hRadius, hR, r | The horizontal radius entities will be hit in around the projectile | 1.25 |
|VerticalRadius | vRadius, vR | The vertical radius entities will be hit in around the projectile |Horizontal Radius |
| MaxDuration | md      | The max duration (in ticks) the projectile will persist              | 100     |
| MaxRange  | mr        | The maximum range (in blocks) the projectile will travel             | 40      |
| Velocity  | v         | The velocity of the projectile                                       | 5       |
| StartYOffset | syo    | Lets you offset where on the casting mob the projectile shoots from  | 1       |
| StartFOffset | sfo    | How far in front of the mob the projectile starts                    | 1       |
| TargetYOffset| tyo    | Lets you offset where on the target the projectile shoots at         | 1       |
| HitPlayers   | hp     | If the missile should hit players                                    | true    |
| HitNonPlayers| hnp    | If the missile should hit non player entities                        | false   |
| HitTarget | ht        | If the missile should be able to hit its target                      | true    |
| HitTargetOnly|        | If the missile should be able to hit **only** its target             | true    |
| StopAtEntity | sE     | Whether the projectile will stop upon hitting a targetable entity    | true    |
| StopAtBlock  | sB     | Whether the projectile will stop upon hitting an opaque block        | true    |
| PowerAffectsRange |par| Whether a mob's [power level](/mythiccraft/MythicMobs/-/wikis/Mobs/Power) affects the projectile's range                                                                 | true    | 
| PowerAffectsVelocity|pav| Whether a mob's [power level](/mythiccraft/MythicMobs/-/wikis/Mobs/Power) affects the projectile's velocity                                                              | true    | 
| fromOrigin | fo       | Whether the missile should start from its origin                     | false   |
| hitConditions |       | A list of conditions that a target must meet in order for the projectile to be able to hit it. See the [projectile](/mythiccraft/MythicMobs/-/wikis/skills/mechanics/projectile) mechanic for more info. **Premium Only** Mechanic                                                       |         |
| Bounces   | bounce    | Should the projectile bounce. Bounce radius depends on the projectile's hitbox. **Premium Only**.                                                                              | false   |
| BounceVelocity | bv   | Every time the projectile bounces, its velocity will be multiplied by this value. **Premium Only** .                                                                      | 0.9     |
| HugSurface| hs        | Whether or not the projectile should move along the ground.          | false   |
| HugLiquid | hugwater, huglava | when using hugSurface will also move on top of liquids       | false   |
| HeightFromSurface| hfs| For NORMAL projectiles, how high above the surface the projectile should glide if HugSurface is set to TRUE. For METEOR projectiles, how high above the surface the projectile starts above the target.                                                                              | 0.5     |
| MaxClimbHeight | mch  | The number of attempts the projectile will make to **increase** its y-location before terminating itself, when the projectiles is "hugging" either a block or a liquid        | 3       |
| MaxDropHeight  | mdh  | The number of attempts the projectile will make to **decrease** its y-location before terminating itself, when the projectiles is "hugging" either a block or a liquid        | 10      |
| highAccuracyMode | ham| Whether to use high-accuracy mode, which raytraces every tick to ensure the projectile cannot ever go anything. Values can be `true`, `false`, `PLAYERS_ONLY`         | PLAYERS_ONLY |

## Examples
This example shoots a missile that looks like a thin trail of flames
with a high turning rate. It bursts into a powerful explosion upon
hitting its target.
```yaml
# Mob File
Mob:
  Type: ZOMBIE
  Skills:
  - skill{s=Homer} @target ~onTimer:100
```
```yaml
# Skills File
Homer:
  Skills:
  - missile{ot=Homer_TICK;oh=Homer_HIT;v=4;i=1;hR=1;vR=1;in=0.75}

Homer_TICK:
  Skills:
  - effect:particles{p=flame;a=1} @origin

Homer_HIT:
  Skills:
  - effect:particles{p=lava;a=50;hS=1;vS=1}
  - effect:sound{s=entity.generic.explode;v=1;p=0}
  - damage{a=1337;i=false}
```