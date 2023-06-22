As seen in the [Skills] wiki page, it is possible to execute mechanics from a mob via the syntax

```yaml
- mechanic{argument=value} @[targeter] ~on[trigger] [health_modifier] [chance]
```

But this approach is not suitable if one wanted to "group together" multiple mechanics and, in general, make more advanced behaviors for the mob. This can be solved via the use of the Metaskills.


Table of Contents:  

[[_TOC_]]

# What is a Metaskill?
A Metaskill is, in essence, a list of mechanics to execute once the metaskill is called via a [Meta Mechanic].  
**They are located in `../plugins/MythicMobs/Skills` inside `.yml` files**, just like their mobs counterpart.  

The syntax of a Metaskill is the following:
```yaml
internal_skillname:
  Cooldown: [seconds]
  OnCooldownSkill: [the metaskill to execute if this one is on cooldown]
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

Once you have a metaskill configured, you can use a [Meta Mechanic], such as [Skill], to execute the Metaskill either from a mob or a metaskill:
```yaml
#MOB FILE
ExampleMob:
  Type: ZOMBIE
  Skills:
  - skill{s=internal_skillname} @self ~onInteract
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
The true core of a metaskill. It's the list of the mechanics that will be executed by the metaskill once triggered. Other [Meta Mechanic]s can be used in here, allowing the Metaskill to trigger other ones. 

```yaml
ExampleSkill:
  Skills:
  - message{m="Hello there!"}
  - skill{s=ExampleSkill_2}

ExampleSkill_2:
  Skills:
  - message{m="How are you doing?"}
```

Delays can also be used here, allowing the user to set a delay for every mechanic in the list after the delay mechanic is used.  

```yaml
ExampleSkill:
  Skills:
  - message{m="Message 1"}
  - delay 20
  - message{m="Message 2"}
```

The skills are normally executed from the first on the list to the last one. If a [Meta Mechanic] is used, its mechanics will be executed before the mechanics of the original Metaskill resume execution. If a delay is present inside the called Metaskill, the mechanics of the original Metaskill resume execution, and the mechanics present in the called metaskill are executed after the delay

![](https://i.imgur.com/ZiHWeBQ.png)
> In this image, an example of the above behavior is shown. If we execute `ExampleSkill_First`, the mechanics will be executed in the order of their numeration, from mechanic1 to mechanic9, with a delay of 20 ticks between mechanic7, mechanic8 and mechanic9


# Targets Inheritance and Override
A peculiarity of Metaskills is their ability to "remember" the targets that were passed to it by the [Meta Mechanic] that called it. This behavior can have many uses and applications.

## Inheritance
Mechanics inside the Metaskill that do not have a targeter of their own will then **Inherit** those targets, and target them.

```yaml
#MOB FILE
ExampleMob:
  Type: ZOMBIE
  Skills:
  - skill{s=ExampleSkill} @PIR{r=10} ~onInteract
```
```yaml
#SKILL FILE
ExampleSkill:
  Skills:
  - ignite
```
In this example, the `ignite` mechanic has no targeter, so it "inherits" the one that was used in the metaskill and target those entities instead, making it ignite all players in a 10 blocks radius.  


## Override
Meanwhile, if a targeter *is* specified inside a Metaskill, we say that the original targeter is **Overridden**, and the new targeter is used instead

```yaml
#MOB FILE
ExampleMob:
  Type: ZOMBIE
  Skills:
  - skill{s=ExampleSkill} @PIR{r=10} ~onInteract
```
```yaml
#SKILL FILE
ExampleSkill:
  Skills:
  - ignite
  - message{m="Why are you so close?"} @NearestPlayer{r=1}
```
In this example, all players will still be ignited, but only the closest player to the mob in a one block radius will receive the message


## Subsequent Metaskills Executions
When you are calling a metaskill from another metaskill, it is still quite possible to not specify a targeter to it, and it will inherit the targets that the calling metaskill also inherited.

```yaml
#MOB FILE
ExampleMob:
  Type: ZOMBIE
  Skills:
  - skill{s=ExampleSkill} @PIR{r=10} ~onInteract
```
```yaml
#SKILL FILE
ExampleSkill:
  Skills:
  - skill{s=Example_Ignite}
  - skill{s=Example_Message} @NearestPlayer{r=1}

Example_Ignite:
  Skills:
  - ignite

Example_Message:
  Skills:
  - message{m="Why are you so close?"}
```
By executing this skill, you will obtain the same results you obtained in the [previus example](Skills/Metaskills#override)


## Targets Filtering
Another great application of target inheritance is the possibility of filtering out the inherited targets across multiple metaskills, using the Metaskill's TargetConditions.

```yaml
#MOB FILE
ExampleMob:
  Type: ZOMBIE
  Skills:
  - skill{s=ExampleSkill_1} @PIR{r=10} ~onInteract
```
```yaml
ExampleSkill_1:
  Skills:
  - message{m="Hello there!"}
  - delay 1
  - skill{s=ExampleSkill_2}

ExampleSkill_2:
  TargetConditions:
  - distance{d=<5} true
  Skills:
  - message{m="...You are pretty close, aren't you?"}
  - delay 1
  - skill{s=ExampleSkill_3}

ExampleSkill_3:
  TargetConditions:
  - distance{d=<1} true
  Skills:
  - message{m="AHHHHHH, GET AWAY FROM ME!"}
  - throw{v=10;vy=2}
```
The above skill will show a message to all the players in a 10 blocks radius, then show another message to those, among them, that are closer than 5 blocks. After that, it will show a third message and push away every player closer than one block.


And now, for a more counter-intuitive example:
```yaml
#MOB FILE
ExampleMob:
  Type: ZOMBIE
  Skills:
  - skill{s=ExampleSkill_1} @PIR{r=10} ~onInteract
```
```yaml
ExampleSkill_1:
  Skills:
  - message{m="Hello there!"}
  - delay 100
  - skill{s=ExampleSkill_2}

ExampleSkill_2:
  TargetConditions:
  - distance{d=>10} true
  Skills:
  - message{m="...You truly don't like me, don't you?"}
  - delay 20
  - message{m="Don't worry, it's fine."}
  - delay 20
  - message{m="I'm used to it."}
  - delay 20
  - message{m="T.T"}
```
In this instance, the mob will first send a message to every player in a 10 blocks radius, and then, 5 seconds later, it will send additional messages to those, among them, that have moved to be more than 10 blocks away in the meantime


## Meta Targeters
Another relevant topic is that of [Meta Targeter]s. Those are targeters that, simply put, will evaluate what the inherited targets are and, based on that, return other appropriate targets themselves.

```yaml
#MOB FILE
ExampleMob:
  Type: ZOMBIE
  Skills:
  - skill{s=ExampleSkill} @PIR{r=10} ~onInteract
```
```yaml
ExampleSkill:
  Skills:
  - effect:particles @Line{r=0.2}
```
The example above, for instance, will generate a line of particles between the caster and the players in a 10 blocks radius. Had the targeter not been `@PIR` but another one, the line would have been generated between the caster and the targeter used.


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
[Skill]: /skills/mechanics/skill
[Meta Targeter]: /Skills/Targeters#special-targeters

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