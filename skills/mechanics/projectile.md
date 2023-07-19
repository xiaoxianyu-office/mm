## Description
The Projectile skill fires a meta-"projectile" that can be decorated
using particle and sound effects.  
It's great for creating complex, aesthetically pleasing skills, such as
shadow bolts, balls of ice, or even meteors.  
It has a lot of options(more than any other skill) and can be a bit of a
nightmare to jump into without knowing what you're doing.  
It will disappear after reached targeted entity or location.  

It is of importance to note that other mechanics (such as [Missile](/skills/mechanics/missile)) are an "extension" of this mechanic, and can as such use a great deal of this mechanic's attributes. The attributes that those mechanics can use are listen in [Inheritable Attributes](/skills/mechanics/projectile#inheritable-attributes)


## Attributes
### Inheritable Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onStartSkill | onStart, oS | Meta-Skill executed when the projectile starts at the projectile's origin location.                                                                                      |         |
| onTickSkill  | onTick, oT  | Meta-Skill executed every [interval] ticks at the projectile's origin location                                                                                       |         |
| onHitSkill   | onHit, oH   | Meta-Skill executed when the projectile hits entities that allow be hit. Targets hit are inherited by the meta-skill.                                                   |         |
| onEndSkill   | onEnd, oE   | Meta-Skill executed when the projectile ends.                   |         |
| onBounceSkill| onBounce    |Meta-Skill executed when the projectile bounces. **Premium Only**.|        |
| onHitBlockSkill |onHitBlock, ohb | Meta-Skill executed when the projectile hits a block.     |         |
| onInteractSkill |onInteract| Meta-Skill executed when the projectile is interacted with.     |         |
| BulletType   | bullet, b   | The type of the bullet. If set, additional attributes becomes available depending on the specified bullet type. A list of bullet types and associated attributes is available [below](/skills/mechanics/projectile#projectile-bullets)                                       | NONE    |
| Interval  | int, i      | How often (in ticks) the projectile updates its position           | 1       |
| HorizontalRadius | hRadius, hR, r | The horizontal radius entities will be hit in around the projectile.                                                                                                                                    | 1.25    |
| VerticalRadius   | vRadius, vR | The vertical radius entities will be hit in around the projectile.                                                                                                                                      | 1.25    |
| Duration  | maxDuration, md, d | The max duration (in ticks) the projectile will persist.    | 400     |
| MaxRange  | mr        | The maximum range (in blocks) the projectile will travel.            | 40      |
| Velocity  | v         | The velocity of the projectile                                       | 5       |
| DeathDelay| death, dd | Delays the removal of project bullets when the projectile is terminated | 2    |
| StartYOffset | syo    | Lets you offset where on the casting mob the projectile shoots from. | 1       |
| StartFOffset | forwardoffset, sfo |  How far in front of the mob the projectile starts       | 1       |
| TargetYOffset | tyo   | Lets you offset where on the target the projectile shoots at.        | 0       |
| SideOffset | soffset, so | The value of this attribute gets inherited by StartSideOffset and EndSideOffset if no value is specified for them                                                | 0       |  
| StartSideOffset | ssoffset, sso | How far to the side of the mob the projectile starts      |sideoffset|
| EndSideOffset | endoffset, esoffset, eso | How far to the side of the target location the projectile will end up                                                                                   |sideoffset|
| startingdirection | startingdir, startdir, sdir | Start direction of the projectile. For now, it only works if inherited by a missile mechanic                                                      |@Targeted|
| HorizontalOffset | hO | Horizontal Offset will rotate the projectile's horizontal starting velocity around a 360-degree axis                                                                      | 0        |
| VerticalOffset   | vO | Vertical Offset will rotate the projectile's vertical starting velocity around a 360-degree axis                                                                               | 0        |
| Accuracy  | ac, a     | Determines the accuracy of the projectile                           | 1        |
| HorizontalNoise | hn  | The randomness of the projectile in horizontal direction            |(1-ac)*45 |
| VerticalNoise   | vn  | The randomness of the projectile in the vertical direction          |(1-ac)*4.5|
| StopAtEntity | sE     | Whether the projectile will stop upon hitting a targetable entity   | true     |
| StopAtBlock  | sB     | Whether the projectile will stop upon hitting an opaque block       | true     |
| PowerAffectsRange |pa | Whether a mob's [power level](/Mobs/Power) affects the projectile's range| true|
| PowerAffectsVelocity | pav | Whether a mob's [power level](/Mobs/Power) affects the projectile's velocity.                                                                                     | true     |
| Interactable |        | Whether the projectile is interactable                              | false    |
| HitSelf   |           | Whether the projectile can hit the caster                           | false    |
| HitPlayers | hp       | Whether the projectile can hit players                              | true     |
| HitNonPlayers | hnp   | Whether the projectile can hit non player entities                  | false    |
| HitTarget | ht        | Whether the projectile can hit the mechanic's target                | true     |
| HitTargetOnly | hto   | Whether the projectile can **only** hit the mechanic's target       | false    |
| ImmuneDelay | immune, id | Sets the immunity delay (when the target can be hit by the projectile again) | 2000  |
| hitConditions | conditions, cond, c | A list of conditions that a target must meet in order for the projectile to be able to hit it. **Premium Only** Mechanic  |  |
| fromorigin | fo       | Whether the projectile should start from the origin of the mechanic | false    |
| requireLineOfSight | rlos, los | Whether the starting point must have line-of-sight to the origin.  Values can be `true`, `false`, `PLAYERS_ONLY`                                             | PLAYERS_ONLY |
| drawHitbox |          | Draw the hitbox of the projectile, useful for debugging             | false    |
| tickinterpolation | interpolation, ti | Interpolates the specified amount of additional points between each tick of the projectile. The onTick and onHit skills will be applied there as well. Useful to fill in the gaps with super-fast projectiles and also prevent entities from being "skipped over"      | 0        |

### Projectile-Specific Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| Type      |           | The "type" of projectile. Default projectiles are launched from the mob's location towards the target. METEOR type projectiles fall from the sky above the target.       | NORMAL  |
| gravity   | g         | Determines the gravity of the projectile; use fractions (0.1-0.2) for low gravity                                                                                        | 0       |
| Bounces   | bounce    | Should the projectile bounce. Bounce radius depends on the projectile's hitbox. **Premium Only**.                                                                              | false   |
| BounceVelocity | bv   | Every time the projectile bounces, its velocity will be multiplied by this value. **Premium Only** .                                                                      | 0.9     |
| HugSurface| hs        | Whether or not the projectile should move along the ground.          | false   |
| HugLiquid | hugwater, huglava | when using hugSurface will also move on top of liquids       | false   |
| HeightFromSurface| hfs| For NORMAL projectiles, how high above the surface the projectile should glide if HugSurface is set to TRUE. For METEOR projectiles, how high above the surface the projectile starts above the target.                                                                              | 0.5     |
| MaxClimbHeight | mch  | The number of attempts the projectile will make to **increase** its y-location before terminating itself, when the projectiles is "hugging" either a block or a liquid        | 3       |
| MaxDropHeight  | mdh  | The number of attempts the projectile will make to **decrease** its y-location before terminating itself, when the projectiles is "hugging" either a block or a liquid        | 10      |
| highAccuracyMode | ham| Whether to use high-accuracy mode, which raytraces every tick to ensure the projectile cannot ever go anything. Values can be `true`, `false`, `PLAYERS_ONLY`         | PLAYERS_ONLY |


## Special Notes

**For the <u>onStart</u> Skill:** onStart skills work in a special way -
any buff or "special effect" mechanics fired by onStart that have a
duration (such as ParticleTornado) will attach to the projectile for
their duration, which allows for some interesting effects.

**For the <u>onTick</u> Skill:** using the **@origin** targeter will
cause any skills or effects to target the projectile's location. This is
the intended way to configure how the projectile looks.

**For the <u>onHit</u> Skill:** Any targets the projectile hits are
passed to the skill inherently. Any targeters you put in the onHit skill
will *override* these and cause your skill to likely not work as you
intend.

**For the <u>onEnd</u> Skill:** Special effects for the projectile's end
also use **@origin**. Also, If you want entities near the end-point of
the projectile to be hit in a certain way (such as a final large
fireball explosion) you can use the **@PlayersNearOrigin{r=[radius]}**
targeter.

**Types:**  
There are two types of projectiles, the normal variant and also the
Meteor variant.  
Meteor projectiles are created above the target, rather than at the mob
that is firing the projectile.  
Because of this, meteor projectiles cannot use certain attributes (which
ones are pending further testing).


## Projectile Bullets

The bullet type that will represent the projectile. These can be specified via the BulletType attribute.
These work with the projectile, missile, and orbital mechanics.

| BulletType  | Aliases      | Description                                                               |
|-------------|--------------|---------------------------------------------------------------------------|
| [ARROW][]   |              | The bullet will be a minecraft projectile                                 |
| [BLOCK][]   |              | The bullet will be a block                                                |
| [SMALLBLOCK][]|            | The bullet will be a small block                                          |
| [ITEM][]    | MYTHICITEM   | The bullet will be an item                                                |
| [MOB][]     |              | The bullet will be a mob. If a Mythicmobs, it will retain its skills      |
| [TRACKING][]| ARMOR_STAND, ARMORSTAND, PSTAND | The bullet will be an item, but its rotation will be adjusted depending on the projectile's direction                                                         |
| [REALTRACKING][] | RTRACKING, REAL_ARMOR_STAND, REALARMORSTAND, STAND | As above, but a real armor stand will also be spawned instead of a packet |
| [DISPLAY][] |              | The projectile will be a display entity                                   |
| [TEXT][]    |              | The projectile will display a line of text                                |

Examples:
```yaml
  - projectile{bulletType=ARROW;arrowType=TRIDENT;...}
  - projectile{bulletType=BLOCK;material=STONE;...}
  - projectile{bulletType=ITEM;material=MyMythicItem;...}
  - projectile{bulletType=MOB;mob=SkeletonKing;...}
```

[ARROW]: /skills/mechanics/projectile#arrow-bullet
[BLOCK]: /skills/mechanics/projectile#block-bullet
[SMALLBLOCK]: /skills/mechanics/projectile#smallblock-bullet
[ITEM]: /skills/mechanics/projectile#item-bullet
[MOB]: /skills/mechanics/projectile#mob-bullet
[TRACKING]: /skills/mechanics/projectile#tracking-bullet
[REALTRACKING]: /skills/mechanics/projectile#realtracking-bullet
[DISPLAY]: /skills/mechanics/projectile#display-bullet
[TEXT]: /skills/mechanics/projectile#text-bullet

### Universal Bullet Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletforwardoffset | bulletfo, bulletoffset | The offset of the bullet                      | 1.8     |

### ARROW Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| arrowtype | bulletarrowtype | The type of the projectile to use. Can be `NORMAL`,`SPECTRAL`,`TRIDENT` | NORMAL |

### BLOCK Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet                                  | STONE   |
| bulletspin | bspin    | The spin of the bullet                                               | 0       |
| audience  |           | The [Audience][] of the bullet                                       | world   |

### SMALLBLOCK Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet                                  | STONE   |
| audience  |           | The [Audience][] of the bullet                                       | world   |

### ITEM Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet                                  | STONE   |
|bulletModel| model     | The CustomModelData of the material                                  | 0       |
|bulletColor|           | The color of the material, if applicable                             |         |
| bulletmatchdirection | bmd | Should the bullet face where the projectile is facing           | false   |
| bulletEnchanted | enchanted | Should the material be enchanted                               | false   |
| audience  |           | The [Audience][] of the bullet                                       | world   |

### MOB Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| mob       | mobType, mm | The mob of the bullet                                       | SkeletalKnight |
| bulletspin | bspin    | The spin of the bullet                                               | 0       |
| bulletmatchdirection | bmd | Should the bullet face where the projectile is facing           | false   |
| bulletKillable | bk   | Allow other entities to damage the projectile bullet                 | false   |
| bulletOffset| boffset | The offset of the bullet mob                                         | 1.35    | 

### TRACKING Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet                                  | STONE   |
|bulletModel| model     | The CustomModelData of the material                                  | 0       |
|bulletColor|           | The color of the material, if applicable                             |         |
| bulletEnchanted | enchanted | Should the material be enchanted                               | false   |
| pitch     |           | The pitch rotation                                                   | 0       |
| yaw       |           | The yaw rotation                                                     | 0       |
| roll      |           | The roll rotation                                                    | 0       |
| rotation  | rot       | The rotation of the bullet, in the x,y,z format                      | 0,0,0   |
| pitchspeed| ps        | The pitch rotation speed                                             | 0       |
| yawspeed  | ys        | The yaw rotation speed                                               | 0       |
| rollspeed | rs        | The roll rotation speed                                              | 0       |
| rotationspeed | rotspeed, rots | The rotation speed of the bullet, in the x,y,z format      | 0,0,0   |
| audience  |           | The [Audience][] of the bullet                                       | world   |

### REALTRACKING Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet                                  | STONE   |
|bulletModel| model     | The CustomModelData of the material                                  | 0       |
|bulletColor|           | The color of the material, if applicable                             |         |
| bulletEnchanted | enchanted | Should the material be enchanted                               | false   |

### DISPLAY Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet                                  | STONE   |
|bulletModel| model     | The CustomModelData of the material                                  | 0       |
|bulletColor|           | The color of the material, if applicable                             |         |
| bulletEnchanted | enchanted | Should the material be enchanted                               | false   |
| pitch     |           | The pitch rotation                                                   | 0       |
| yaw       |           | The yaw rotation                                                     | 0       |
| roll      |           | The roll rotation                                                    | 0       |
| rotation  | rot       | The rotation of the bullet, in the x,y,z format                      | 0,0,0   |
| pitchspeed| ps        | The pitch rotation speed                                             | 0       |
| yawspeed  | ys        | The yaw rotation speed                                               | 0       |
| rollspeed | rs        | The roll rotation speed                                              | 0       |
| rotationspeed | rotspeed, rots | The rotation speed of the bullet, in the x,y,z format       | 0,0,0   |
| rollspeed | rs        | The roll rotation speed                                              | 0       |
| tx        |           | The translation on the x axis                                        | 0       |
| ty        |           | The translation on the y axis                                        | 0       |
| tz        |           | The translation on the z axis                                        | 0       |
| translation | pos, offset | The translations on the axes, in the x,y,z format                | 0,0,0   |
| hideFirstTick | hft   | Hides the item for the first tick                                    | false   |
|bulletscale| scale     | The scale of the bullet                                            |0.5,0.5,0.5|
| audience  |           | The [Audience][] of the bullet                                       | world   |

### TEXT Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletText| text      | The text of the bullet                                               | *       |
| bulletBillboard | billboard | The [billboard type][] of the bullet                           | CENTER  |
|bulletscale| scale     | The scale of the bullet                                            |0.5,0.5,0.5|
| backgroundcolor | color | The Background color, in the ARGB format                          | 64,0,0,0 |
| audience  |           | The [Audience][] of the bullet                                       | world   |


[Audience]: /Skills/Effects#audience
[billboard type]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Display.Billboard.html

<!--
Bullet types available are:

- **ARROW** - *projectile{bulletType=ARROW;arrowType=(NORMAL/SPECTRAL/TRIDENT);...}*
- **BLOCK** - *projectile{bulletType=BLOCK;material=STONE;...}*
- **ITEM** - *projectile{bulletType=ITEM;material=STONE;...}*
- **MYTHICITEM** - *projectile{bulletType=MYTHICITEM;material=MyMythicItem;...}*
- **MOB** - *projectile{bulletType=MOB;mob=SkeletonKing;...}*
- **TRACKING** - *projectile{bulletType=TRACKING;bulletmaterial=MyMythicItem;model=CustomModelData;...}*
- **DISPLAY** - *projectile{bulletType=DISPLAY;...}* `same options as tracking/armorstand bullet`
- **TEXT** - *projectile{bulletType=TEXT;bulletText="...";bulletBillboard=CENTER;bulletscale=1.0,1.0,1.0;backgroundColor=64,0,0,0;...}*
  - `backgroundColor` - this is expressed in argb format

Yes, that's right, you can even shoot projectiles made up of other
Mythic mobs! Mobs shot with the projectile skill cannot be interacted
with, but will still use all their skills...

You can also use the new **bulletSpin=#** option to give your bullets
some spin.
-->

## Examples

This example shoots a fast-moving ball of ice that damages and slows the
first entity it hits:  
**Mob File**  
```yaml
Mob:
  Type: SKELETON
  Skills:
  - skill{s=IceBolt} @target ~onTimer:100
```
**Skills File**  
```yaml
IceBolt:
  Skills:
  - projectile{onTick=IceBolt-Tick;onHit=IceBolt-Hit;v=8;i=1;hR=1;vR=1;hnp=true}
IceBolt-Tick:
  Skills:
  - effect:particles{p=snowballpoof;amount=20;speed=0;hS=0.2;vS=0.2} @origin
IceBolt-Hit:
  Skills:
  - damage{a=10}
  - potion{type=SLOW;duration=100;lvl=2}
```
hitConditions usage example:
```yaml
  - projectile{hitConditions=[  - isMonster true  - isFrozen false ]}
```