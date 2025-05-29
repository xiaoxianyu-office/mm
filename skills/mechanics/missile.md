## Description
The missile mechanic is similar to the projectile mechanic and can use any of the [Projectile's Inheritable Attributes](/skills/mechanics/projectile#inheritable-attributes).  
Missiles however are homing and will track down their targets.
Missiles can target both a location and an entity.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| Inertia   | in, intertia | Sets the "turning-rate" of the missile. Lower values make the missile turn around faster. Use big numbers (10-100) when trying to make your missiles turn slowly.         | 1.5     |
| Bounces   | bounce    | Should the projectile bounce. Bounce radius depends on the projectile's hitbox. **Premium Only**.                                                                              | false   |
| BounceVelocity | bv   | Every time the projectile bounces, its velocity will be multiplied by this value. **Premium Only** .                                                                      | 0.9     |
| startWithParentVelocity | swpv, spv | Whether the missile, if called from another projectile, should start with the same velocity as the parent projectile                                          | false   |
| HugSurface| hs        | Whether or not the projectile should move along the ground.          | false   |
| HugLiquid | hugwater, huglava | when using hugSurface will also move on top of liquids       | false   |
| HeightFromSurface| hfs| For NORMAL projectiles, how high above the surface the projectile should glide if HugSurface is set to TRUE. For METEOR projectiles, how high above the surface the projectile starts above the target.                                                                              | 0.5     |
| MaxClimbHeight | mch  | The number of attempts the projectile will make to **increase** its y-location before terminating itself, when the projectiles is "hugging" either a block or a liquid        | 3       |
| MaxDropHeight  | mdh  | The number of attempts the projectile will make to **decrease** its y-location before terminating itself, when the projectiles is "hugging" either a block or a liquid        | 10      |
| highAccuracyMode | ham| Whether to use high-accuracy mode, which raytraces every tick to ensure the projectile cannot ever go through anything. Values can be `true`, `false`, `PLAYERS_ONLY`         | PLAYERS_ONLY<!--type:Projectile_HighAccuracyMode-->|
| hitnonplayers | hnp   | Whether the missile should hit non player entities                   | true    |

> This mechanic inherits every inheritable attribute of the [Projectile](/skills/mechanics/projectile#inheritable-attributes) mechanic
>> - The `hitnonplayers ` attribute is **defaulted** at `true`


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


## Aliases
- [x] mi


<!--TAGS-->
<!--tag:Projectile-->