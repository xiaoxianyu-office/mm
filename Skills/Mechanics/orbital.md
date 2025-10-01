## Description

The Orbital skill fires a special type of
[projectile](/skills/mechanics/projectile) that will orbit around the
target and can also act as an [Aura](/skills/mechanics/aura), inheriting all of its attributes. Like the
projectile, it will trigger other skills on anyone that is hit by it
during its orbit.  
Much like projectile, it's great for creating complex skills, such as a
fire shield, and is a very complex skill to master.  

Added projectile bullets to Orbital in MM 4.11. See how to use them on the [projectiles mechanic](/skills/mechanics/projectile) page.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onHit     | oH, onhitskill | Meta-Skill executed when the projectile hits something. Targets hit are inherited by the meta-skill                                                                    |<!--type:Metaskill-->|
| radius    | r         | The radius of the orbit around the target                            | 4       |
| hitRadius | hr        | The radius around the orbital in which targets can be hit            | 1       |
| verticalHitRadius | vhr, vr | The y component of the hitradius                           | `hitradius` |                                                                                                                       
| points    | p         | How many "points" that comprise the circle that makes up the orbit. More points will make the circle more defined, but will also increase the time it takes to complete an orbit  | 32   |
| startingpoint | sp    | The starting step of the orbital aura                                | 0       |
| tickinterpolation | interpolation, ti | Interpolates additional points between each tick of the projectile, running onTick multiple times                                                      | 0       |
| rotationx | rotx, rx  | Rotates the orbital along the X axis. Rotation is done in radians, i.e. `3.14` is half a rotation, `6.28` is a full rotation                                                  | 0       |
| rotationy | roty, ry  | Rotates the orbital along the Y axis. Rotation is done in radians, i.e. 3.14 is half a rotation, 6.28 is a full rotation                                                       | 0       |
| rotationz | rotz, rz  | Rotates the orbital along the Z axis. Rotation is done in radians, i.e. 3.14 is half a rotation, 6.28 is a full rotation                                                       | 0       |
| offsetx   | ox, offx  | Offsets the orbital along the X axis of the target                   | 0       |
| offsety   | oy, offy  | Offsets the orbital along the Y axis of the target                   | 0       |
| offsetz   | oz, offz  | Offsets the orbital along the Z axis of the target                   | 0       |
| angularVelocityX | avx, vx | Modifies the angular velocity of the orbital on the X axis      | 0       |
| angularVelocityY | avy, vy | Modifies the angular velocity of the orbital on the Y axis      | 0       |
| angularVelocityZ | avz, vz | Modifies the angular velocity of the orbital on the Z axis      | 0       |
| rotate    |           | Whether the orbital should rotate                                    | true    |
| reversed  | reverse, backwards | Whether the orbital should rotate in the opposite direction | false   |
| hitPlayers       | hp | Whether can hit players                                              | true    |
| hitNonPlayers    | hnp| Whether can hit non players                                          | false   |
| hitSelf          | hs | Whether can hit caster                                               | false   |
| hugsurface       | hs      | Whether or not the orbital should move along the ground         | false   |
| hugliquid        | hugwater, huglava | Whether using `hugSurface` will also make the orbital move on top of liquids                                                                                     | false   |
| heightfromsurface | hfs    | How high above the surface the orbital should glide if `HugSurface` is set to `true`                                                                                      | 0.5     |
| maxclimbheight   | mch     | The number of attempts the projectile will make to **increase** its y-location by 1 before terminating itself, when the projectiles is "hugging" either a block or a liquid| 3 |
| maxdropheight | mdh        | The number of attempts the projectile will make to **decrease** its y-location by 1 before terminating itself, when the projectiles is "hugging" either a block or a liquid| 10|
| bullettype    | bullet, b  | The [Projectile Bullet Type](/skills/mechanics/projectile#projectile-bullets). Also makes the orbital inherits every related attribute                               | NONE<!--type:Projectile_BulletType-->|
| castAsOrbital | cao        | Whether the metaskills should be casted by the orbital itself rather than from the caster, as Projectiles do                                                              | false  |
| immunedelay | immune, iD | Sets the immunity delay (when the target can be hit by the projectile again) | 2000 |
| drawhitbox |  | Draw the hitbox of the orbital, useful for debugging | false |
| hitconditions | conditions, cond, c | A list of conditions that a target must meet in order for the orbital to be able to hit it. **Premium Only** Mechanic | <!--type:Conditions--> |
| stopconditions | stpcond | A list of conditions that a target must meet in order for the orbital to end when hitting them | <!--type:Conditions--> |
| hitTargeter | htr     | An entity targeter. Once the orbital hits, targeted entities will be targeted by the onHit Metaskill and given immune delay just like the orbital's main target          | <!--type:Targeter--> |
| shareSubHitboxCooldown | shcd | Whether all meg sub hitboxes should share the same immune delay with its base entity | true | 


> This mechanic inherits every attribute of the [Aura](/skills/mechanics/aura) mechanic
  

### onStart Attribute
onStart skills work in a special way - any buff or "special effect" mechanics fired by onStart that have a
duration (such as ParticleTornado) will attach to the projectile for their duration, which allows for some interesting effects.

### onTick Attribute
Using the **@origin** targeter will cause any skills or effects to target the projectile's location. This is the intended way to configure how the projectile looks.

### onHit Attribute
Any targets the projectile hits are passed to the skill inherently. Any targeters you put in the onHit skill will *override* these and cause your skill to likely not work as you intend.

### onEnd Attribute
Special effects for the projectile's end also use **@origin**. Also, If you want entities near the end-point of the projectile to be hit in a certain way (such as a final large fireball explosion) you can use the **@PlayersNearOrigin{r=[radius]}** targeter.


## Examples
This example puts an icy-looking orbital shield around the mob when it
is hit sometimes, that will last for 10 seconds or until it is triggered
once:  
```yaml
# Mob File
Mob:
  Type: SKELETON
  Skills:
  - skill{s=IceShield} @self ~onDamaged 0.2
```
```yaml
# Skills File
IceShield:
  Skills:
  - orbital{onTick=IceShield-Tick;onHit=IceShield-Hit;points=20;interval=1;duration=200;charges=1}
IceShield-Tick:
  Skills:
  - effect:particles{p=snowballpoof;amount=20;speed=0;hS=0.2;vS=0.2} @origin
IceShield-Hit:
  Skills:
  - damage{a=10}
  - potion{type=SLOW;duration=100;lvl=2}
```

##

This example shows how the orbital can be removed via the [Auraremove](`auraremove`) mechanic.
<br>The mob `ExampleMob` create the shield from the previous example once it gets damaged with a 20% chance, but unlike the previous example this time the orbital also has an auraName attribute. When the mob receives a REMOVESHIELD signal, he will both remove the orbital via the auraremove mechanic and the orbital's auraName while also sending a SHIELDREMOVED signal back to the trigger of the metaskill

```yaml
# Mob File
ExampleMob:
  Type: ZOMBIE
  Skills:
  - skill{s=IceShield} @self ~onDamaged 0.2
  - skill{s=IceShield-Remove} @self ~onSignal:REMOVESHIELD
```

```yaml
# Skills File
IceShield:
  Skills:
  - orbital{
    auraName=IceShield;
    onTick=IceShield-Tick;onHit=IceShield-Hit;points=20;interval=1;duration=200;charges=1}

IceShield-Remove:
  Skills:
  - auraremove{aura=IceShield}
  - signal{s=SHIELDREMOVED} @trigger
```


## Aliases
- [x] o


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
<!--tag:Projectile-->
