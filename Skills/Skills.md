Skills are an integral feature of MythicMobs.
All mobs (and items if you have the [Crucible] add-on) are able to have skills of various types that can be triggered under different circumstances with varying
conditions. The MythicMob skill system is quite intuitive once you get used to it, and can be used to create anything from simple mobs to incredibly complex bosses.

Skills are made up of several distinct parts:

-   [Mechanics]
-   [Targeters]
-   [Triggers]
-   [Conditions]


# Getting Started

So what makes a skill?

Skills are made up of [skill mechanics][Mechanics], or "base skills", which are simple basic skills by themselves that come with MythicMobs. Each skill mechanic is called in the **Skills** section of a mob. Lets take a look at an example of what this looks like:

```yaml
FieryZombie:
  Type: ZOMBIE
  Display: 'Fiery Zombie'
  Health: 50
  Skills:
  - mechanic1
  - skill{skill=Skill1}
  - skill{s=Skill2}
  - skill:Skill3
  - etc
```

Each skill mechanic is assigned to the mob in a list such as the one
above. But what would a real mechanic look like? Here's a real example:
```yaml
FieryZombie:
  Type: ZOMBIE
  Display: 'Fiery Zombie'
  Health: 50
  Skills:
  - ignite{ticks=100} @target ~onAttack <50% 0.5
```

Yikes! What does all of that mean? Let's take a look at what makes up
this skill:

```yaml
Skills:
- mechanic{argument=value} @[targeter] ~on[trigger] [health_modifier] [chance]
```

This may still look pretty intimidating, but each part by itself is very
simple, and some are even optional. Lets break each part down
separately!


## Mechanics

The first, and most important part of a skill, is the mechanic. This is what you want to happen, it is the base skill you are performing. It may be dealing damage, or setting something on fire, or striking lightning. [There are many different mechanics][Mechanics] you can use, but they are composed of two main types: mechanics that target entities, and mechanics that target a location. Some can target both, or neither.

Most mechanics also have arguments. These come directly after the mechanic name and are surrounded in curly-braces {}. Each argument is separated by a semi-colon (;). Each mechanic has its own arguments, all of which can be found on the [Mechanics] wiki page.

```yaml
Skills:
- mechanic{option1=value;option2=value;option2=value;...}
```

You can also expand the syntax to be more readable if you prefer, but keeping the correct indentation is very important or YAML will be upset. Below is a format I would personally recommend for both its clarity and neatness.

```yaml
Skills:
- mechanic{option=value;
           option=value;
           option=value}
```

Setting up a mechanic is as simple as identifying the mechanic you want to use and plugging in the options you want. Most options have a default value and are optional. So if you wanted to set someone on fire for 5 seconds, you'd use the ignite mechanic and set the "ticks" option to 100 (there are 20 ticks in a second):

```yaml
Skills:
- ignite{ticks=100}
```


## Targeters

Targeters are another core part of implementing skills. Targeters are "what you want the skill to be aimed at". There are many types of targeters, and most can be categorized into targeting "Entities" or "Locations". It is important to choose the right targeter for what you want to do. [Here is a list of all the targeters].

Targeters go directly after the mechanic in your skill line, and are always prefixed with an @ symbol. Some can also have their own options, which also go in curley braces after the targeter.

```yaml
    Skills:
    - mechanic{option=value} @targeter{option1=value;option2=value;...}
```

Going back to our previous example, lets say you want it to set the mob's target on fire. You'd simply do this...

```yaml
Skills:
- ignite{ticks=100} @target
```

Or perhaps you want it to set ALL players nearby on fire. Let's say within a 5 blocks radius...

```yaml
Skills:
- ignite{ticks=100} @PlayersInRadius{radius=5}
```

Essentially, the targeter is what you want to the mechanic to hit.


## Triggers

Triggers are also a very important part of skills. Triggers determine "what causes this skill to happen".

Triggers go directly after the targeter, and generally start with **~on** followed by the trigger name.

```yaml
Skills:
- mechanic{option=value} @targeter{option=value} ~onTrigger
```

Going back to our previous example, lets say you want this trigger to fire when the mob attacks its target, so its melee attacks apply fire also.

```yaml
Skills:
- ignite{ticks=100} @target ~onAttack
```

Some targeters also work hand-in-hand with certain triggers. For example, the @Trigger targeter targets whatever entity triggered the skill. In the example below, the player who right-clicks the mob (interacts with the mob) will be set on fire, as they are the @Trigger.

```yaml
Skills:
- ignite{ticks=100} @Trigger ~onInteract
```

**Note: Items have a different set of Triggers. [Click here to see which triggers work with Crucible].**


## Health Modifiers

Health modifiers are a special type of condition that come after the trigger. These allow you to easily set health ranges at which skills will execute, and are entirely optional to add. Health modifiers come in several simple forms. Here are some examples:

-   **=90%** - The skill will only trigger when the mob is below 90% health. Please note, using this modifier will cause the skill to only ever trigger once.
-   **&lt;50%** - The skill will only trigger when the mob is below 50% health.
-   **=30%-50%** - The skill will only trigger when the mob is between 30% and 50% health.
-   **&lt;2000** - The skill will only trigger when the mob is below 2000 Health.
-   **&gt;500** - The skill will only trigger when the mob is above 500 Health.

Health Modifiers go directly after the trigger and are prefixed with either **=**, **&lt;**, or **&gt;**, depending on the range you want to use.

```yaml
Skills:
- mechanic{option=value} @targeter{options=value} ~onTrigger =/</> HealthModifier
```

Going back to our previous example, lets say you want the skill to only work when the mob is below 50% health:

```yaml
Skills:
- ignite{ticks=100} @target ~onAttack <50%
```

## Chance

Chance is another simple and optional conditional you can add onto skill lines. Chance is always the last thing you put on the skill line, and is a simple decimal number where 1.0 is 100%, 0.5 is 50%, and 0 is 0%.

So to wrap up the example, lets say you want this trigger to only fire on 50% of melee attacks while below 50% health: 

```yaml
Skills:
- ignite{ticks=100} @target ~onAttack <50% 0.5
```

# Wrapping it all Up

As you can see, while the original skill looked intimidating, breaking it down into pieces makes things much simpler.

Once you get the hang of using individual base-skills, you can use Meta-Skills to combine them into more complex skills. This will be covered in a later article.

  [Crucible]: https://git.mythiccraft.io/mythiccraft/mythiccrucible
  [Mechanics]: /Skills/Mechanics/
  [Targeters]: /Skills/Targeters/
  [Triggers]: /Skills/Triggers/
  [Conditions]: /Skills/conditions/
  [Here is a list of all the targeters]: /Skills/Targeters/
  [Click here to see which triggers work with Crucible]: https://git.mythiccraft.io/mythiccraft/mythiccrucible/-/wikis/Skills/Triggers

# Cheat Sheet
![image](uploads/ebf67740e7bc604db56a95cf62397030/image.png)
> You can use this fabulous schema made by the fantastic [ShenKuro](https://discord.com/users/695202854134218763)