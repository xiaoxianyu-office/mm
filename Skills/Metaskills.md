As seen in the [Skills] wiki page, itis possible to execute mechanics from a mob via the syntax

```yaml
- mechanic{argument=value} @[targeter] ~on[trigger] [health_modifier] [chance]
```

But this approach is not suitable if one wanted to "group together" multiple mechanics and, in general, make more advanced behaviors for the mob. This can be solved via the use of the Metaskills.


Table of Contents:  

[[_TOC_]]

# What is a Metaskill?
A Metaskill is, in essence, a list of mechanics to execute once the metaskill is called via a [Meta Mechanic].  
They are located in `../plugins/MythicMobs/Skills` inside `.yml` files.  

The syntax of a Metaskill is the following:
```yaml
internal_skillname:
  Cooldown: [seconds]
  OnCooldownSkill: [the metaskill to execute if this on is on cooldown]
  CancelIfNoTargets: [true/false]
  Conditions:
  - condition1
  - condition2
  TargetConditions:
  - condition3
  - condition4
  TriggerConditions:
  - condition5
  - condition6
  Skills:
  - mechanic1
  - mechanic2
```

Please note that only the `internal_skillname` element is required. For instance, you could make a Metaskill with only skills, only a cooldown, or only some Conditions.

In the following paragraphs it will be explained what every element in there does, and how to use it.
There are also a couple of pertinent [Examples] if you want to see a more practical usage.

# Breaking Down the Metaskills Configuration

## Internal SkillName
It's the string that will identify the metaskill inside mythicmobs, exactly how the [Internal Name] works for mobs.

A valid Internal SkillName must be unique (aka, there cannot exists two skills that shares the skillname) and not containt any space character.

If you want to execute a specific metaskill in any way, you will have to use its Internal SkillName in some way


## Cooldown
The Cooldown is the time, in seconds, that must elapse between executions of the metaskill for the same caster.  

For instance:
```yaml
ExampleCooldownSkill:
  Cooldown: 10
  Skills:
  - ignite @self
```
The `ExampleCooldownSkill` metaskill will only be able to be triggered once every 10 seconds by the same caster.

A cooldown can be:
- **tested against** via the [SkillOnCooldown] condition
- **fetched** via the [<caster.skill.\[skill_name\].cooldown>] placeholder
- **set** via the [SetSkillCooldown] mechanic.


## OnCooldownSkill
If the Metaskill is triggered while on cooldown, the skill specified here will be casted instead.

For instance, in this example:
```yaml
FirstSkill:
  Cooldown: 10
  OnCooldownSkill: SecondSkill
  Skills:
  - command{c="say First"}

SecondSkill:
  Cooldown: 5
  OnCooldownSkill: ThirdSkill
  Skills:
  - command{c="say Second"}

ThirdSkill:
  Skills:
  - command{c="say Third"}
```
Casting FirstSkill normally would result in "First" being written in chat. Executing it again while still on cooldown would write "Second" in chat, and executing it another time while both FirstSkill and SecondSkill are on cooldown would result in "Third" being written in chat


## CancelIfNoTargets
If the metaskill should cancel its execution if no eligible targets are provided to it.  
Defaults to `true`.


## Conditions
The [Conditions] of the metaskill. Those conditions evaluates the caster of the metaskill.

Depending on the [Condition Action] used in each condition, different behaviors can occur: read the relevant wiki page for more info


## TargetConditions
The Target [Conditions] of the metaskill. Those conditions evaluates the inherited target of the metaskill, it being either an entity ot a location.

Depending on the [Condition Action] used in each condition, different behaviors can occur: read the relevant wiki page for more info

## TriggerConditions
The Trigger [Conditions] of the metaskill. Those conditions evaluates the entity that triggered the skilltree. This entity can also be targeted via the [@Trigger] targeter

Depending on the [Condition Action] used in each condition, different behaviors can occur: read the relevant wiki page for more info


## Skills
The true core of a metaskill. It's the list of the mechanics that will be executed by the metaskill once triggered. Other [Meta Mechanic]s can be used in here, allowing the Metaskill to trigger other ones. Delays can also be used here, allowing the user to set a delay for every mechanic in the list after the delay mechanic is used.  

The skills are normally executed from the first on the list to the last one. If a [Meta Mechanic] is used, its mechanics will be executed before the mechanics of the original Metaskill resume execution. If a delay is present inside the called Metaskill, the mechanics of the original Metaskill resume execution, and the mechanics present in the called metaskill are executed after the delay

![](https://i.imgur.com/ZiHWeBQ.png)
> In this image, an example of the above behavior is shown. If we execute `ExampleSkill_First`, the mechanics will be executed in the order of their numeration, from mechanic1 to mechanic9, with a delay of 20 ticks between mechanic7, mechanic8 and mechanic9


# Skill Parameters [Premium Feature]

Skill parameters are a feature allowing you to more easily create generic skills and pass parameters to them from other skills. If that sounds confusing, here's an example!

Currently most people have a lot similar damage skills that are just tweaked a bit for all their different mobs for slight variances in damage, but they do basically the same thing otherwise.

**The old way of doing it:**
```yaml
#SKILL FILE
ShadowDamage20:
  Skills:
  - damage{amount=20}
  - some shadowy effect

#MOB FILE
Mob1:
  Skills:
  - skill{s=ShadowDamage20} ~onAttack
```

**With Skill Parameters, we can combine these all into a single skill! The new way:**
```yaml
#SKILL FILE
ShadowDamage:
  Skills:
  - damage{amount=<skill.damage>}

#MOB FILE
Mob1:
  Skills:
  - skill{s=ShadowDamage;damage=20} ~onAttack
```

In the example above, the skill will still deal 20 damage to the target, we've just made the skill generic so that we can change the damage however we please on any mob.  
The "skill parameter" system will pass __any__ options from the **skill/metaskill** mechanic (except options that are specific to it) down the skill tree where you can reference them later. If a later skill passes the same parameter, it will overwrite it. These can be used anywhere placeholders are supported.


<!-- GENERIC -->
[Skills]: /Skills/Skills
[Meta Mechanic]: /Skills/Mechanics#advancedmeta-mechanics
[Examples]: /examples/Common-Examples#skills

<!-- INTERNAL SKILLNAME -->
[Internal MobName]: /Mobs/Mobs#internal_name

<!-- COOLDOWN -->
[SkillOnCooldown]: /conditions/skilloncooldown
[<caster.skill.\[skill_name\].cooldown>]: /Skills/Placeholders#caster-placeholders
[SetSkillCooldown]: /skills/mechanics/setskillcooldown

<!-- CONDITIONS -->
[Conditions]: /Skills/conditions
[Condition Action]: /Skills/conditions#condition-actions
[@Trigger]: /Skills/Triggers#the-trigger-targeter