MythicMobs contains a lot of different features and terms which are important to learn. This page gives a brief description of all the different things.

## Mobs
### Options
### Custom AI
### Equipment
### Drops

## Mechanics
[Mechanics Wiki](/Skills/Mechanics)

Mechanics are the main way to add interesting and unique abilities to the mobs you create. The most basic way to use a mechanic is to add it to your mobs Skills section along with a trigger and targeter, but you can also add them in MetaSkills. Most mechanics have a list of attributes which can be used with them to modify how they work.

`- giveitem{i=DIAMOND;cd=10} @NearestPlayer ~onTimer:20`

## Targeters
[Targeters Wiki](/Skills/Targeters)

Targeters are what tell your mechanics who to target. For example if you are using the giveitem mechanic, the targeter will decide who to give the item to.

`- giveitem{i=DIAMOND;cd=10} @NearestPlayer ~onTimer:20`

## Triggers
[Triggers Wiki](/Skills/Triggers)

Triggers tell your mobs when to activate their mechanics and abilities. Triggers must start with a `~` and be placed after the Targeter. Triggers can only be put directly on your mobs, they will not work if written in a MetaSkill. In the example, `~onTimer:20` is the trigger, telling the mechanic to run every 20 ticks (1 second)

`- giveitem{i=DIAMOND;cd=10} @NearestPlayer ~onTimer:20`

## Attributes
Attributes are the information you can pass to a mechanic to customize how it works. In this example `cd=10` and `m=testing` are the attribute, telling the mechanic the item to give and to have a cooldown of 10 seconds. Attributes are seperated by a `;` symbol and must have a `=` before what you set.

`- giveitem{i=DIAMOND;cd=10} @NearestPlayer ~onTimer:20`

## Conditions
[Conditions Wiki](/Skills/Conditions)

Conditions allow you to limit how things are executed. You can do inline conditions or use the conditions section wherever you are using them.


## MetaSkills
[MetaSkills Wiki](/Skills/Metaskills)

Skills are a fundamental feature of MythicMobs, they allow you to combine multiple mechanics into one giving you the ability to create interesting attacks and functions with multiple effects and visuals.

## Items
[Items Wiki](/Items/Items)

## RandomSpawns
[RandomSpawns Wiki](/Random-Spawns)

## Spawners
[Spawners Wiki](/Spawners)

## Variables
[Variables Wiki](/Skills/Variables)