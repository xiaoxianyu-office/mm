## Description
The Projectile skill fires a meta-"projectile" that can be decorated
using particle and sound effects.  
It's great for creating complex, aesthetically pleasing skills, such as
shadow bolts, balls of ice, or even meteors.  
It has a lot of options (more than any other mechanic) and can be a bit of a
nightmare to jump into without knowing what you're doing.  
It will disappear after hitting an entity or location that is able to stop the projectile. This behavior can be configured via attributes like `stopatblock`, `stopatentity` and `stopconditions`

It is of importance to note that other mechanics (such as [Missile](/skills/mechanics/missile) and [Totem](/skills/mechanics/totem)) are an "extension" of this mechanic, and can as such use a great deal of this mechanic's attributes. The attributes that those mechanics can use are listen in [Inheritable Attributes](/skills/mechanics/projectile#inheritable-attributes)

[[_TOC_]]

## Attributes
### Inheritable Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onStartSkill | onStart, oS | Meta-Skill executed when the projectile starts at the projectile's origin location.                                                                                      |<!--type:Metaskill-->|
| onTickSkill  | onTick, oT, m, meta, s, skill | Meta-Skill executed every [interval] ticks at the projectile's origin location                                                                                       |<!--type:Metaskill-->|
| onHitSkill   | onHit, oH   | Meta-Skill executed when the projectile hits entities that are allowed be hit. Targets hit are inherited by the meta-skill.                                              |<!--type:Metaskill-->|
| onEndSkill   | onEnd, oE   | Meta-Skill executed when the projectile ends.                   |<!--type:Metaskill-->|
| onBounceSkill| onBounce    |Meta-Skill executed when the projectile bounces. **Premium Only**.|<!--type:Metaskill-->|
| onHitBlockSkill |onHitBlock, ohb | Meta-Skill executed when the projectile hits a block.     |<!--type:Metaskill-->|
| onInteractSkill |onInteract| Meta-Skill executed when the projectile is interacted with.     |<!--type:Metaskill-->|
| BulletType   | bullet, b   | The type of the bullet. If set, additional attributes becomes available depending on the specified bullet type. A list of bullet types and associated attributes is available [below](/skills/mechanics/projectile#projectile-bullets)                                       | <!--type:Projectile_BulletType-->|
| Interval  | int, i      | How often (in ticks) the projectile updates its position           | 1       |
| HorizontalRadius | hRadius, hR, r | The horizontal radius entities will be hit in around the projectile.                                                                                                                                    | 1.25    |
| VerticalRadius   | vRadius, vR | The vertical radius entities will be hit in around the projectile.                                                                                                                                      | 1.25    |
| Duration  | maxDuration, md, d | The max duration (in ticks) the projectile will persist.    | 400     |
| MaxRange  | mr        | The maximum range (in blocks) the projectile will travel.            | 40      |
| Velocity  | v         | The velocity of the projectile, expressed in blocks traveled per second| 5     |
| DeathDelay| death, dd | Delays the removal of project bullets when the projectile is terminated | 2    |
| StartYOffset | syo    | Lets you offset where on the casting mob the projectile shoots from. | 1       |
| StartFOffset | forwardoffset, sfo |  How far in front of the mob the projectile starts       | 1       |
| TargetYOffset | tyo, targety | Lets you offset where on the target the projectile shoots at. | 0       |
| SideOffset | soffset, so | The value of this attribute gets inherited by StartSideOffset and EndSideOffset if no value is specified for them                                                | 0       |  
| StartSideOffset | ssoffset, sso | How far to the side of the mob the projectile starts      |sideoffset|
| EndSideOffset | endoffset, esoffset, eso | How far to the side of the target location the projectile will end up                                                                                   |sideoffset|
| startingdirection | startingdir, startdir, sdir | Start direction of the projectile. For now, it only works if inherited by a missile mechanic                                                      |@Targeted<!--type:Targeter-->|
| HorizontalOffset | hO | Horizontal Offset will rotate the projectile's horizontal starting velocity around a 360-degree axis                                                                      | 0        |
| VerticalOffset   | vO | Vertical Offset will add a [slope](https://en.wikipedia.org/wiki/Grade_(slope)) to the projectile's starting direction. To give it a specific angle, you can use [this image](https://en.wikipedia.org/wiki/Grade_(slope)#/media/File:Slope_quadrant.svg) as reference: the value you need will be the number shown in red divided by 100 (so if you want 40°, you will need to input 83.9/100 = `0.839`)| 0        |
| Accuracy  | ac, a     | Determines the accuracy of the projectile                           | 1        |
| HorizontalNoise | hn  | The randomness of the projectile in horizontal direction            |(1-ac)*45 |
| VerticalNoise   | vn  | The randomness of the projectile in the vertical direction          |(1-ac)*4.5|
| StopAtEntity | sE     | Whether the projectile will stop upon hitting a targetable entity   | true     |
| StopAtBlock  | sB     | Whether the projectile will stop upon hitting an opaque block       | true     |
| PowerAffectsRange | par | Whether a mob's [power level](/Mobs/Power) affects the projectile's range| true|
| PowerAffectsVelocity | pav | Whether a mob's [power level](/Mobs/Power) affects the projectile's velocity.                                                                                     | true     |
| Interactable |        | Whether the projectile is interactable                              | false    |
| HitSelf   |           | Whether the projectile can hit the caster                           | false    |
| HitPlayers | hp       | Whether the projectile can hit players                              | true     |
| HitNonPlayers | hnp   | Whether the projectile can hit non player entities                  | false    |
| HitTarget | ht        | Whether the projectile can hit the mechanic's target                | true     |
| HitTargetOnly | hto   | Whether the projectile can **only** hit the mechanic's target       | false    |
| ImmuneDelay | immune, id | Sets the immunity delay (when the target can be hit by the projectile again) | 2000  |
| hitConditions | conditions, cond, c | A list of conditions that a target must meet in order for the projectile to be able to hit it. **Premium Only** Mechanic  |<!--type:Conditions-->|
| stopconditions | stpcond | A list of conditions that a target must meet in order for the projectile to end when hitting them                                                                         | null     |
| doEndSkillOnHit | esoh | Whether the onEnd metaskill should be run when the projectile ends by hitting an entity | true |
| fromorigin | fo       | Whether the projectile should start from the origin of the mechanic | false    |
| requireLineOfSight | rlos, los, requirelos | Whether the starting point must have line-of-sight to the origin.  Values can be `true`, `false`, `PLAYERS_ONLY`                                             | PLAYERS_ONLY<!--type:Projectile_HighAccuracyMode-->|
| drawHitbox |          | Draw the hitbox of the projectile, useful for debugging             | false    |
| tickinterpolation | interpolation, ti | Interpolates the specified amount of additional points between each tick of the projectile. The onTick and onHit skills will be applied there as well. Useful to fill in the gaps with super-fast projectiles and also prevent entities from being "skipped over"      | 0        |
| shareSubHitboxCooldown | shcd | Whether all meg sub hitboxes should share the same immune delay with its base entity | true | 
| hitTargeter | htr     | An entity targeter. Once the projectile hits, targeted entities will be targeted by the onHit Metaskill and given immune delay just like the projectile's main target          | <!--type:Targeter--> |

### Projectile-Specific Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| Type      |           | The "type" of projectile. Default projectiles are launched from the mob's location towards the target. METEOR type projectiles fall from the sky above the target.       | NORMAL<!--type:Projectile_Type-->|
| gravity   | g         | Determines the gravity of the projectile; use fractions (0.1-0.2) for low gravity                                                                                        | 0       |
| Bounces   | bounce    | Should the projectile bounce. Bounce radius depends on the projectile's hitbox. **Premium Only**.                                                                              | false   |
| BounceVelocity | bv   | Every time the projectile bounces, its velocity will be multiplied by this value. **Premium Only** .                                                                      | 0.9     |
| HugSurface| hs        | Whether or not the projectile should move along the ground.          | false   |
| HugLiquid | hugwater, huglava | when using hugSurface will also move on top of liquids       | false   |
| HeightFromSurface| hfs| For NORMAL projectiles, how high above the surface the projectile should glide if HugSurface is set to TRUE. For METEOR projectiles, how high above the surface the projectile starts above the target.                                                                              | 0.5     |
| MaxClimbHeight | mch  | The number of attempts the projectile will make to **increase** its y-location before terminating itself, when the projectiles is "hugging" either a block or a liquid        | 3       |
| MaxDropHeight  | mdh  | The number of attempts the projectile will make to **decrease** its y-location before terminating itself, when the projectiles is "hugging" either a block or a liquid        | 10      |
| highAccuracyMode | ham| Whether to use high-accuracy mode, which raytraces every tick to ensure the projectile cannot ever go through anything. Values can be `true`, `false`, `PLAYERS_ONLY`         | PLAYERS_ONLY<!--type:Projectile_HighAccuracyMode-->|


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
| [ITEM][]    | MYTHICITEM   | The bullet will be an item or MythicItem                                  |
| [MOB][]     |              | The bullet will be a mob. If a Mythicmobs, it will retain its skills      |
| [TRACKING][]| ARMOR_STAND, ARMORSTAND, PSTAND | The bullet will be an item, but its rotation will be adjusted depending on the projectile's direction                                                         |
| [REALTRACKING][] | RTRACKING, REAL_ARMOR_STAND, REALARMORSTAND, STAND | As above, but a real armor stand will also be spawned instead of a packet |
| [DISPLAY][] |              | The projectile will be a display entity                                   |
| [TEXT][]    |              | The projectile will display a line of text                                |
| [ME][]      | MEG, MODELENGINE | The projectile will be a [ModelEngine] model                          |

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
[ME]: /skills/mechanics/projectile#me-bullet
[ModelEngine]: /../../../model-engine-4/-/wikis

### Universal Bullet Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletforwardoffset | bulletfo, bulletoffset, bfo | The offset of the bullet                 | 1.8     |
| bulletYOffset | byo   | The Y offset of the bullet                                           | 0       | 

### ARROW Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| arrowtype | bulletarrowtype | The type of the projectile to use. Can be `NORMAL`,`SPECTRAL`,`TRIDENT` | NORMAL<!--type:NORMAL,SPECTRAL,TRIDENT--> |

### BLOCK Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet                                  | STONE<!--type:Block--> |
| bulletspin | bspin    | The spin of the bullet                                               | 0       |
| audience  |           | The [Audience][] of the bullet                                       | world<!--type:Audience--> |

### SMALLBLOCK Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet                                  | STONE<!--type:Material--> |
| audience  |           | The [Audience][] of the bullet                                       | world<!--type:Audience--> |

### ITEM Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet, either a vanilla item type or custom MythicItem    | STONE<!--type:Item-->  |
|bulletModel| model     | The CustomModelData integer for the material (define model strings on a MythicItem instead)   | 0       |
|bulletColor|           | The color of the material, if applicable                             |         |
| bulletmatchdirection | bmd, bulletsmall | Should the bullet face where the projectile is facing | false |
| bulletEnchanted | enchanted | Should the material be enchanted                               | false   |
| audience  |           | The [Audience][] of the bullet                                       | world<!--type:Audience--> |

### MOB Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| mob       | mobType, mm | The mob of the bullet                         | SkeletalKnight<!--type:Mob-->|
| bulletspin | bspin    | The spin of the bullet                                               | 0       |
| bulletmatchdirection | bmd | Should the bullet face where the projectile is facing           | false   |
| bulletKillable | bk   | Allow other entities to damage the projectile bullet                 | false   |
| bulletYOffset| byo | The Y offset of the bullet mob                                          | 1.35    | 
| bulletForwardOffset| bfo| The forward offset of the bullet mob                               | 1.35    | 

### TRACKING Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet, can be vanilla item type or MythicItem     | STONE<!--type:Item--> |
|bulletModel| model     | The CustomModelData integer for the material (define model strings on a MythicItem instead)  | 0       |
|bulletColor|           | The color of the material, if applicable                             |         |
| bulletEnchanted | enchanted | Should the material be enchanted                               | false   |
| pitch     |           | The pitch rotation, in radians                                       | 0       |
| yaw       |           | The yaw rotation, in radians                                         | 0       |
| roll      |           | The roll rotation, in radians                                        | 0       |
| rotation  | rot       | The rotation of the bullet in radians, in the x,y,z format           | 0,0,0   |
| pitchspeed| ps        | The pitch rotation speed                                             | 0       |
| yawspeed  | ys        | The yaw rotation speed                                               | 0       |
| rollspeed | rs        | The roll rotation speed                                              | 0       |
| rotationspeed | rotspeed, rots | The rotation speed of the bullet, in the x,y,z format      | 0,0,0   |
| audience  |           | The [Audience][] of the bullet                                       | world<!--type:Audience--> |

### REALTRACKING Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat | The material of the bullet, can be vanilla item type or MythicItem | STONE<!--type:Item--> |
|bulletModel| model     | The CustomModelData integer for the material (define model strings on a MythicItem instead) | 0       |
|bulletColor|           | The color of the material, if applicable                             |         |
| bulletEnchanted | enchanted | Should the material be enchanted                               | false   |

### DISPLAY Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletmaterial | material, mat, bulletitem | The material of the bullet, can be vanilla item type or MythicItem  | STONE<!--type:Item--> |
|bulletModel| model     | The model of the bullet                                              |         |
|bulletcustommodeldata| custommodeldata, cmd | The CustomModelData integer for the material    | 0       |
|bulletColor|           | The color of the material, if applicable                             |         |
| bulletEnchanted | enchanted | Should the material be enchanted                               | false   |
|bulletscale| scale     | The scale of the bullet                                            |0.5,0.5,0.5|
| bulletyoffset | byoffset, byo | The y offset of the bullet                                   | 0.2     |
| bulletBillboarding | bulletBillboard | The [billboard type] of the bullet                    | FIXED   |
| bulletbrightness | bulletbrightnessblock | The bullet's brightness                           | -1      |
| bulletbrightnesssky | | The bullet's sky light brightness                           | bulletbrightness |
| bulletCullingDistance | bulletViewDistance, bulletViewRange | The range in which the bullet will be visible                                                                                        | 50      |
| pitch     |           | The pitch rotation, in radians                                       | 0       |
| yaw       |           | The yaw rotation, in radians                                         | 0       |
| roll      |           | The roll rotation, in radians                                        | 0       |
| rotation  | rot       | The rotation of the bullet in radians, in the x,y,z format           | 0,0,0   |
| pitchspeed| ps        | The pitch rotation speed                                             | 0       |
| yawspeed  | ys        | The yaw rotation speed                                               | 0       |
| rollspeed | rs        | The roll rotation speed                                              | 0       |
| rotationspeed | rotspeed, rots | The rotation speed of the bullet, in the x,y,z format       | 0,0,0   |
| tx        |           | The translation on the x axis                                        | 0       |
| ty        |           | The translation on the y axis                                        | 0       |
| tz        |           | The translation on the z axis                                        | 0       |
| translation | pos, offset | The translations on the axes, in the x,y,z format                | 0,0,0   |
| hideFirstTick | hft   | Hides the item for the first tick                                    | false   |
| bulletCullingHeight | cullHeight | The bullet's display culling height                       | 0.0     |
| bulletCullingWidth | cullWidth | The bullet's display culling width                          | 0.0     |
| audience  |           | The [Audience][] of the bullet                                       | world<!--type:Audience--> |
| bulletgen | generation, bulletgeneration | If MythicCrucible is installed, the generation option for the bullet item |

### ME Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletModel | model   | The MEG model to use for the bullet                                  |         |
| bulletstate | state   | The state to play for the MEG model                                  |         |
| bulletcolor |         | The tint of the bullet's model                                       |         |
| bulletscale |         | The scale of the bullet                                              | 1       |
| bulletEnchanted | enchanted | Whether the bullet's model should be enchanted                 | false   | 
| bulletGlowing | glowing | Whether the bullet's model should be glowing                       | false   |
| bulletglowcolor |     | The glow color of the bullet, if `bulletGlowing` is set to true      |         |
| bulletCulling  | culling | Whether to apply culling for the bullet model                     | true    |
| bulletViewRadius |    | From how far the bullet can be seen, if greater than 0.              | -1      |
| bulletBrightness |    | The brightness of the bullet                                         |         |
| bulletalod | alod     | Whether to use LOD culling on the bullet                             | true    |

### TEXT Bullet
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bulletText| text      | The text of the bullet                                               | *       |
| bulletBillboard | billboard | The [billboard type] of the bullet                             | CENTER<!--type:Billboard-->|
|bulletscale| scale     | The scale of the bullet                                            |0.5,0.5,0.5|
| forcedBulletRotation  | forcedRotation | Forces the rotation of the bullet with the specified pitch, yaw and roll, in the x,y,z format. Leave empty to allow the bullet to dynamically rotate based on the travel direction |   |
| bulletRotatesBasedOnDirection | | Whether the text bullet should rotate based on the direction of movement. Might *not* be what you expect | false |
| bulletyoffset | byoffset, byo | The y offset of the bullet                                   | 0       |
| bulletforwardoffset | bulletfo, bulletoffset, bfo | The forward offset of the bullet         | 1.8     |
| backgroundcolor | color | The Background color, in the ARGB format                          | 64,0,0,0 |
| bulletCullingDistance | bulletViewDistance, bulletViewRange | The range in which the bullet will be visible                                                                                        | 50      |
| bulletCullingHeight | cullHeight | The bullet's display culling height                       | 0.0     |
| bulletCullingWidth | cullWidth | The bullet's display culling width                          | 0.0     |
| bulletBrightness | bulletBrightnessBlock | The bullet's brightness, if the value is > -1     | -1      |
| bulletBrightnessSky| |The bullet's sky light brightness, if the value is > -1                | -1      |
| audience  |           | The [Audience][] of the bullet                                       | world<!--type:Audience--> |


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


## Aliases
- [x] p


<!-- LINKS -->
[Audience]: /Skills/Audience
[billboard type]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Display.Billboard.html


<!--TAGS-->
<!--tag:Projectile-->
<!--tag:Meta-Mechanic-->