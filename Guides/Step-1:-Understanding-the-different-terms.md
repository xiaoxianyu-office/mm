MythicMobs contains a lot of different features and terms which are important to learn. This page gives a brief description of all the different things you may encounter while working on your mobs.

## Mobs
[Mobs Wiki](/Mobs/Mobs)

As the name of the plugin suggests, mobs are the most important, core component of MythicMobs.

### Options
[Mob Options Wiki](/Mobs/Options)

Mob Options allow you to change various settings about your mob. Not all mobs can use all the options so check the wiki page to see what can be used for what mob types.

### Custom AI
[Custom AI Wiki](/Mobs/Custom-AI)

Custom AI lets you change how your mob behaves by default. You can make them choose different targets, and act a different way towards them. Custom AI is made up of 2 selectors, Goals and Targets.

Goals: Determine what your mob does, such as running from players, floating in water and attacking.

Targets: Determine who or what your mob targets, such as Players and other mobs.

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
Attributes are the information you can pass to a mechanic to customize how it works. In this example `cd=10` and `i=DIAMOND` are the attribute, telling the mechanic the item to give and to have a cooldown of 10 seconds. Attributes are seperated by a `;` symbol and must have a `=` before what you set.

`- giveitem{i=DIAMOND;cd=10} @NearestPlayer ~onTimer:20`

## Conditions
[Conditions Wiki](/Skills/Conditions)

Conditions allow you to limit how things are executed. You can do inline conditions or use the conditions section wherever you are using them.


## MetaSkills
[MetaSkills Wiki](/Skills/Metaskills)

Skills are a fundamental feature of MythicMobs, they allow you to combine multiple mechanics into one giving you the ability to create interesting attacks and functions with multiple effects and visuals.

## Items
[Items Wiki](/Items/Items)

MythicMobs has the ability to create basic custom items which can be used by mobs or given to players. You can exapnd upon these items if you have the [MythicCrucible](https://mythiccraft.io/index.php?resources/crucible-custom-items-armor-furniture-blocks-more.2/) addon plugin.

## RandomSpawns
[RandomSpawns Wiki](/Random-Spawns)

RandomSpawns are used to make your mobs naturally spawn in your worlds, without the need for commands or spawners. You can add conditions to decide when they spawn.

## Spawners
[Spawners Wiki](/Spawners)

Spawners can be used to spawn mobs periodically at a set location. These can be useful for dungeons or RPG maps. 

Please note: Spawner files CANNOT be edited while the server is running, you must stop your server to edit the files. You can use in-game commands instead.

## Variables
[Variables Wiki](/Skills/Variables)

Variables are a handy system used for storing information. You can then use the information in various other places such as placeholders in mechanics and conditions.