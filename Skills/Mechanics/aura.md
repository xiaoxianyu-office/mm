## Description
The Aura mechanic acts as a status effect on the target entity, and can
trigger other skills over its duration. Auras allow you to create custom
status effects (i.e. buffs and debuffs) that are tracked for their
duration and can also be used in other mechanics and conditions.  

[[_TOC_]]

| [Implemented Placeholders]         |
|------------------------------------|
| `<skill.var.aura-name>`            |
| `<skill.var.aura-type>`            |
| `<skill.var.aura-charges>`         |
| `<skill.var.aura-duration>`        |
| `<skill.var.aura-duration-millis>` |
| `<skill.var.aura-stacks>`          |

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| auraName  | aura, b, buff, buffname, debuff, debuffname, n, name | Optional name, required to use associated mechanics & conditions that reference a specific aura. Given a random UUID if not defined.                            |         |
| components| component, comp  | The aura components to apply. Better explained later in the page |<!--type:AuraComponents--> | 
| auratype  | auragroup, group, type, g | The type of the aura. It's similar to its name       |         |
| tags               | tag     | A list of comma-separated tags that the aura will have. The tags do nothing on their own, but can be used to "mark" the aura and better check against it                    |
| attachmenttype | attachment, attach | The [Attachment](#attachment-types) to apply to the entity the aura is applied to                             | NONE    |
| onStartSkill | onStart, os | Meta-Skill executed when the aura first starts                  |<!--type:Metaskill-->|
| onTickSkill  | onTick, ot  | Meta-Skill executed every [interval] ticks on the affected entity|<!--type:Metaskill-->|
| onEndSkill   | onEnd, oe   | Meta-Skill executed when the aura ends                          |<!--type:Metaskill-->|
| ShowBarTimer | bartimer, bt| If set, the aura will display a bar for caster during it        | false   |
| Charges   | c         | If set, the aura will fade when it hits zero charges. Modifiable by other mechanics.                                                                                     | 0       |
| Duration  | ticks, t, d, time, t | The max duration (in ticks) the aura will persist.        | 200     |
| Interval  | i         | How often (in ticks) the aura fires its onTick skill                 | 1       |
| maxStacks | ms        | How many times the aura stacks on the same targeted entity if applied multiple times                                                                                          | 1       |
| refreshDuration | rd  | Makes the aura's duration refresh to the amount defined in the mechanic should the entity have the same aura applied to it again                                              | true    |
| mergeSameCaster | msc, mc | Merges all auras of the same name applied by one entity to another into one aura (Prevents a mob from being able to stack an aura multiple times on the same entity)            | `false` if any among `mergeAll`, `overwriteAll` or `overwriteSameCaster` is `true` |
| mergeAll        | ma  | Merges all auras of the same name applied by any and all entities to another into one aura (Prevents multiple mobs from being able to stack an aura multiple times on the same entity)| false  |
| overwriteSameCaster | osc, oc | When applied, stops all of the same auras applied on the target by the same caster and replaces them with the new aura (cannot be used with merge options)                                                | false   |
| overwriteAll    | overwrite, ow | When applied, stops all of the same auras applied on the target and replaces them with the new aura  (cannot be used with merge options)                                                                | false   |
| CancelOnGiveDamage | cogd    | Cancels the aura if the entity with the aura deals any damage to another entity                                                                                         | false   |
| CancelOnTakeDamage | cotd    | Cancels the aura if entity with the aura takes any sort of damage|false|
| CancelOnDeath      | cod     | Cancels the aura if the entity with the aura dies             | true    |
| CancelOnCasterDeath| cocd    | Cancels the aura if the caster of the aura dies               | false   |
| CancelOnTeleport   | cot     | Cancels the aura if the entity with the aura teleports at all, whether by another mechanic or server command                                                             | false   |
| CancelOnChangeWorld | cocw    | Cancels the aura if the entity with the aura changes worlds. (Most times applies to players)                                                                            | false   |
| CancelOnSkillUse    | cosu    | Cancels the aura if the entity with the aura uses another skill while the aura is active                                                                             | false   |
| CancelOnQuit        | coq     | Cancels the aura if the entity with the aura logs out. (Only really applies to players)                                                                            | true    |
| DoEndSkillOnTerminate | desot, alwaysrunendskill, ares | Whether or not the aura will run onEndSkill when it's removed by auraremove mechanic                                                       | true    |

## Components
An aura can define multiple components to use. Each defined component can trigger additional metaskills and apply specific features.  

> [!tip]
> If you are familiar with mechanics such as [onDamaged](/Skills/Mechanics/onDamaged) or [onAttack](/Skills/Mechanics/onAttack), then this might sound pretty familiar to you. In fact, those mechanics are just an aura with a single specific component applied to them. But by using proper aura components, you will be able to create an aura that has multiple such effects at the same time!

Components have the same syntax of mechanics, and each has its own specific attributes you can define 

```yaml
  - aura{auraname=MultiAura;duration=200;interval=10;
      components=[
        - onattack{onattack=[ - particles{p=flame;a=50;s=1} @self ]}
        - ondamaged{ondamaged=[ - particles{p=soulflame;a=50;s=1} @self ]}
        - stat{stat=HEALTH;type=ADDITIVE;value=20}
      ]}
```

| Component                                                       | Description                          |
|-----------------------------------------------------------------|--------------------------------------|
| [ChunkLoad](/Skills/Mechanics/AuraComponents/ChunkLoad) | Keeps the chunk the target is in loaded for the duration of the aura  |
| [Fear](/Skills/Mechanics/AuraComponents/Fear)                   | Makes the target run around in fear  |
| [Fly](/Skills/Mechanics/AuraComponents/Fly)             | Makes the target player have creative flight |
| [Glow](/Skills/Mechanics/AuraComponents/Glow)                   | Makes the target glow                |
| [OnAttack](/Skills/Mechanics/AuraComponents/OnAttack) | Applies an aura component to the target that triggers a skill when they damage something. It is also possible to change the damage event itself|
| [OnBlockBreak](/Skills/Mechanics/AuraComponents/OnBlockBreak) | Applies an aura component to the target that triggers a skill when they break a block |
| [OnBlockPlace](/Skills/Mechanics/AuraComponents/OnBlockPlace) | Applies an aura component to the target that triggers a skill when they place a block |
| [OnChat](/Skills/Mechanics/AuraComponents/OnChat) | Applies an aura component on the target player that triggers a metaskill when they type a chat message |
| [OnDamaged](/Skills/Mechanics/AuraComponents/OnDamaged) | Applies an aura component to the target that triggers a skill when they take damage from something. It is also possible to change the damage event itself          |
| [OnDeath](/Skills/Mechanics/AuraComponents/OnDeath) | Applies an aura component to the target that triggers a skill when they die |
| [OnInteract](/Skills/Mechanics/AuraComponents/OnInteract) | Applies an aura component to the target that triggers a skill when they right click an entity/get right clicked by a player |
| [OnSwing](/Skills/Mechanics/AuraComponents/OnSwing) | Applies an aura component to the target player that triggers a skill when they swing their arm (left click) |
| [OnShoot](/Skills/Mechanics/AuraComponents/OnShoot) | Applies an aura component to the target that triggers a skill when they shoot a projectile |
| [Stat](/Skills/Mechanics/AuraComponents/Stat) | Applies an aura component to the target that that applies a specific stat to them |
| [Stun](/Skills/Mechanics/AuraComponents/Stun) | Holds the target in place temporarily |

## Attachment Types
Attachments are optional "objects" that are applied (attached) to the entity the aura is applied to

| Attachment  | Aliases      | Description                                                               |
|-------------|--------------|---------------------------------------------------------------------------|
| [MODELENGINE](#modelengine-attachment) | MEG, ME      | A ModelEngine model                            |

### ModelEngine Attachment
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| attachmentmodel | attachmodel, model | The model of the attachment                           |         |
| attachmentstate | attachstate, state | The state the model will be playing                   |         |
| attachmentcolor | attachcolor | The color applied to the model                               |         |
| attachmentscale | attachscale | The scale of the model                                       | 1       |
| attachmentViewRadius | attackviewradius | The view radius of the model. Leave as -1 to use ModelEngine's default settings | -1 |
| attachmentEnchanted | attachEnchanted, enchanted | Whether the model should have an enchantment glint applied to it | false |
| attachmentGlowing | attachGlowing, glowing | Whether the model should be glowing             | false   |
| attachmentglowcolor | attachglowcolor | The glow color of the model, if `attachmentGlowing` is set to `true` | |
| attachmentCulling | attachCulling, culling | Whether the model should be able to be culled by ModelEngine | true | 
| attachmentoffset | attachoffset | The model's offset from the attached entity, in a `x,y,z,yaw,pitch` format.<br>Can also be written as `x,y,z` or `x,y,z,yaw` | 0,0,0,0,0 |

## ShowBarTimer Attribute
If set to `true`, additional attributes becomes available
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| bartimerdisplay | bartimertext | The text in the bossbar                                    | auraname |
| bartimercolor |       | The [Color](/Mobs/BossBar#color) of the bossbar      | RED<!--type:BarColor--> |
| bartimerstyle |       | The [Style](/Mobs/BossBar#style) of the bossbar    | SOLID<!--type:BarStyle--> |

## Examples
```yaml
  Skills:
  - Aura{auraName=Retributing_Light;onTick=RetributingLightDamage;interval=10;duration=240} @self
```
Gives the target (Which in this case is the entity itself) the
Retributing_Light aura that lasts 12 seconds. Every 10 ticks (or half a
second) it will fire the RetributingLightDamage skill.

---

```yaml
 Skills:
  - onDamaged{auraName=fire_shield;onHit=FireShield;duration=200;charges=5;multiplier=0.5} @self
```
In this example, the caster's next 5 hits taken in 10 seconds would
trigger the FireShield skill targeting whatever hit them and also deal
50% damage. However, if FireShield's conditions failed, it would deal
regular damage as the multiplier would not trigger either.

---

```yaml
  Skills:
  - onAttack{auraName=fiery_strikes;onHit=FireStrike;duration=200;charges=5;multiplier=2} @self
```
In this example, the caster's next 5 physical hits within 10 seconds
would trigger the FireStrike skill targeting whatever was hit and also
deal 200% damage. However, if FireStrike's conditions failed, it would
deal regular damage as the multiplier would not trigger either.


## Aliases
- [x] buff
- [x] debuff


<!-- LINKS -->
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
<!--tag:Meta-Mechanic-->