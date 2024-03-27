5.7.0 (Dev Builds)
=====
- Added new HEARING ability to mobs enabled by `Hearing.Enabled: true`. Requires 1.20+
- Added `~onHear` trigger that responds to hearing sounds

5.6.1
=====
- Added various new config options for items and drops
- Added more tab completion to commands
- Added all the new fancy drop effects for vanilla items
- Added all the new fancy drop effects for MMOItems items
- Added placeholder support to variable keys
- Added some API stuff for item updating
- Added more debugging information when a LibsDisguises disguise throws an error
- Added placeholder support to @Pin targeter
- Added way to use the trigger's stats in DamageModifier stats
- Added Parent stats and capabilities for DamageModifier stat types
- Added `stopCondition` to projectiles
- Added `castasorbital` to orbital
- Rewrote part of spawner saving
- Fixed spawner files not deleting
- Fixed ConcurrentModificationException that could rarely occur when copying spawners
- Fixed plugin not loading on regular spigot - per-player drops require paper
- Fixed fancy drop effects causing items added thru the api to not roll amounts closes #1502
- Fixed mechanics still firing if a death event has been cancelled (does not...
- Fixed recursive issue with cancelevent
- Fixed some spawner command bugs
- Fixed some loading bugs introduced with the change to default lowercase folder names
- Fixed spawner copying not copying the spawner's group
- Fixed `<caster.score.>` placeholder?
- Fixed exit aura spelling`
- Fixed complex stat initialization with formulas and ordering problems
- Allow placeholder on projectile vertical radius
- Fixed vector rotation calculation
- Fixed NPE in ActiveInfo utility command


5.6.0
=====

Highlights
----------
- Rewrote config files. Old settings should automatically migrate and are now located in a new `configs` folder
- Added new `Fancy` Drops Per-Player Loot Drops
- Glow effects no longer requires GlowAPI
- Mob Egg improvements

General
-------
- Improved output of getCoordinates utility command

Configs
-------
- Added new config options for different hologram features and adjusted some settings

Pins
----
- Added & improved some pin commands
- Added `/mm pins toggleviewing` command for holograms
- Added `/mm pins move` command
- Changed `/mm pins list` to sort by nearest pins to you

Mobs
----
- Added `Variables` field to mobs for pre-set variables available to skills
- Added `Nameplate.Mounted: false` option for MEG mobs
- Mob eggs are now fully configurable in `config-mobs.yml` and the display/lore can be overridden on a per-mob basis
```
SomeMob:
  Egg:
    Display: '<caster.name> EGG'
    Lore:
    - 'im a testing egg'
```

Mechanics
---------

### `NEW: followPath`
- Added `followPath mechanic` - an aura causing the target mob to walk along a defined path

### `NEW: modifyDamage`
- Make `modifyDamage` mechanic's default damage type be `ALL`
- Make `modifyDamage` mechanic modify all damage types if `type=ALL`
- Added `modifyDamage` mechanic allowing modification of the damage of the current triggering event

### `Auras`
- Added `cancelOnCasterDeath=true` option to all aura mechanics
- Added debugging info for auras

### `Hide`
- Hide Mechanic now extends Aura
- Added AbstractPlayer#hideEntity and AbstractPlayer#showEntity

### `Hit`
- Added `forcedDamage` to hit mechanic

### `Glow`
- Glow Effect no longer requires GlowAPI
- Glow Effect now extends Aura

### `takeItem`
- Fixed other bugs with `takeItem` mechanic
- Added `exact=false` option to `takeItem` mechanic

Conditions
----------
### `NEW: lookingAt`
- Added lookingAt player condition

### `NEW: originLocation`
- Added `originLocation{location=x,y,z}` condition to match if the origin is at a specific location

Triggers
--------
- Added `onSkillDamage` trigger, triggered by skill damage

Targeters
---------
- Added `bb=false` filter to make a targeter ignore MEG subhitboxes
- Added `unique=false` entity targeter option, setting to false will allow a targeter to hit multiple sub-hitboxes at once on a modeled mob

Placeholders
------------
- Added various `caster.target.` placeholders to act on the target of the caster
- `<trigger.item.amount>` placeholder added

Mob Drops
---------
- Added various new drop options

RandomSpawning
--------------
- Added new options such as `LimitMultiplier` to help control Random Spawning

API
---
- Added PlayerLevelProvider
- Added `MythicMobEggEvent` for when an egg is used

Bugs / Other
------------
- Allowed placeholders in `radius` and `minRadius` attributes in `@RandomLocationsNearTargets` targeter
- Fixed jigsaw structures not working with structure condition
- Fixed NPE in GoToParent goal
- Fixed onDamaged mechanic not working with custom damage types or multi-type damage
- Fixed per-player loot vfx not moving with the loot with fancy drops
- Fixed some backwards compatibility issues with the placeholder refactor
- Fixed bug with hologram culling
- Fixed inline items with skull textures throwing a Bukkit error
- Skills will now try to detect if there's a `cancelevent` mechanic somewhere
- Fixed double placeholders showing a decimal point when rounding=0
- Fixed holograms sometimes appearing in the wrong world
- Fixed target.l.x placeholder
- Fixed `<caster.level>` placeholder to default to rounding to 0 places
- Fixed typo in WorldScaling config parser
- Fixed bug with world scaling
- Fixed a potential bug in TargetInLineOfSight condition
- Fixed crash caused by PreventTeleporting on endermen (closes #1431)
- Fixed some bugs with pins
- Fixed NPE in ActiveMob.checkEquipment
- Fixed bug with using type=ALL with damageMod
- Fixed action attribute in damageMod mechanic
- Fixed recursive damage bug with lightning mechanic on onDamaged trigger
- Fixed recursive damage bug with lightning mechanic on onDamaged trigger (again)
- Fixed some placeholder bugs
- Fixed ClassCastException in mob listener involving vanilla overrides
- Fixed bottleneck with getting a mob's children from an async thread
- Fixed bugs causing placeholders registered from add-ons not processing until after a reload
- Fixed some things in the default stats.yml file
- Fixed for potential memory leak involving random spawners used with MythicDungeons
- Fixed bugs with auras that don't have names set
- Fixed StatAura not giving stats for additional stacks
- Fixed bug in stat displays and keys
- Fixed custom MM nameplates trying to apply to MEG modeled mobs instead of vanilla mobs
- Fixed caster spawn targeter mutating location
- Fixed villager trade 2nd item using 1st count
- Fixed metadata not syncing between subhitbox and parent on MEG mobs
- Fixed projectiles not hitting MEG OBBs
- Fixed look mech pitch and yaw being swapped
- Fixed BlockLight and SkyLight properties
- Fixed event firing before bullets are set
- Fixed guardian beam issues
- Fixed @self targeter sometimes requiring targetself=true which is unintuitive
- Fixed PreventOtherDrops not affecting equipped items closes #1474
- Fixed `<<` for ranges not working with nested placeholders
- Fixed `@playersNearTargetLocations` meta-targeter not working with base entity targets
- Fixed NPE with incorrectly configured mob bullets closes #1481
- Fixed attack speed stat throwing an error on mobs that don't support attack speed closes #1484

5.5.1
=====

General
-------
- Added preliminary 1.20.3 support (not complete, may have version-related bugs)
- Allow broadcast command to parse placeholders
- Added `fromOrigin=true` option to `throw` mechanic
- Change setting default for cancelling zero-damage damage events to false

Conditions
----------
### NEW: `isUsingSpyglass`
### Health
- Added `includeAbsorption` option to `health` condition
### Yaw
- Added `clamp` option to yaw condition to clamp yaw to 0-360, defaults to true

Bugs / Other
------------
- Changed damage trigger listeners to skip zero-damage subclassed events to fix issues with other plugins that use it for PvP checks
- Fixed hasItem condition not detecting custom items added via API
- Fixed NPE in projectiles happening during world unload
- Fixed auras `cancelOnTakeDamage` option not applying to block damage
- Fixed projectile origin facing yaw=0 when `requireLineOfSight=true` 
- Fixed issue where summoning multiple projectiles using fromOrigin=true causes them to stack on top of each other in a line
- Fixed HideFlag to use 127 on versions before 1.20 for backwards compatibility
- Fixed imported items not generating correctly closes #1389

5.5.0
=====

General
-------
- Added `General.CancelDamageIfZero` config option, defaults to true (current behavior)

### Pins System
- Allows locations to quickly be saved in a `pins.yml` file (located in any pack folder)
- Added `/mm pins create [pack] [name]` command to save your current location as a pin
- Added `@Pin{pin=name}` targeter
- Added `inPinRegion{pin1=X;pin2=Y}` condition

Mobs
----
Added new available mythic entity types:
- EXPERIENCE_BOTTLE
- INTERACTION
- ITEM_DISPLAY
- MINECART
- MINECART_CHEST

Added Tamed option for cats

Mechanics
----------
### NEW: `onChat`
- An aura that intercepts the target's next chat message
- Executes a skill after the message is intercepted and passes `<skill.var.input>` as the input

```
- onChat{then=[
    - message{m="Entered <skill.var.input>"}
]}
```

### NEW: `setFlying`
- `setFlying{flying=true}`

### NEW: `setInteractionSize`
- `setInteractionSize{height=X;width=Y}`

### NEW: `summonFallingBlock`
- `summonFallingBlock{material=SAND}`

### Auras
- Added `<skill.var.aura-duration-millis>` placeholder

### `Glow`
- No longer requires GlowAPI on 1.18+ (thanks to Phil)

### `Orbital`
- Added `reversed=true` option to reverse the direction

### `ModifyProjectile`
- Added `YOFFSET` trait, usable with orbitals

### `PickupItem`
- Added `onPickup` (alias `then`) option to the `pickupItem` mechanic to execute a mechanic after an item is picked up

### Speak
- Allow `\n` to force a newline in speech

Conditions
----------
### NEW: `blockTypeInRadius`
- Allows you to check if there are a number of blocks within a certain radius

Example: Check if there are 10 lit furnaces facing north or south within 10 blocks: `blockTypeInRadius{r=10;a=>9;types=minecraft:furnace[lit=true,facing=north],minecraft:furnace[lit=true,facing=south]}`

### NEW: `inPinRegion` 
- Whether the target location is inside a region created between 2 pins
- `inPinRegion{pin1=x;pin2=Y}`

### NEW: `itemType`
- Used when targeting item entities, such as with the ` ItemsInRadius` targeter

### NEW: `triggerBlockType`
- Used with block-related triggers such as ~onBlockBreak

### NEW: `triggerItemType`
- Used with item-related triggers such as ~onItemPickup

### MobsInRadius
- Allow condition to check for vanilla mobs also

Targeters
---------
### NEW: `@InteractionLastAttacker`
- Targets the last person that punched an interaction entity

### NEW: `@InteractionLastInteract`
- Targets the last person that interacted with an interaction entity

### NEW: `@Pin`
- Targets a pinned location defined in a pack's pins.yml
- `@Pin{pin=X}`

### Ring
- Added `relative=true` option to make the ring rotate with the facing of the caster

Placeholders
------------
- Added `<item.amount>` placeholder usable with item-related triggers

Items
-------
- Added support for armor trims using `Options.Trim: material.pattern`
- Added `Author`, `Title`, and `Pages` options for written books

API
---
- Added `MythicPreReloadEvent` - fires before the reload operation begins

Bugs / Other
------------
- Added placeholder support to several missing places
- Fixed problems with display bullet view range
- Fixed various issues with display bullets in 1.20.2
- Fixed an issue with ItemSpray effect
- Fixed `PIG_ZOMBIE` alias not working
- Fixed NPE with stats when mobs spawn
- Fixed item mechanics/conditions only checking for mmoitems type
- Fixed Mythic not handling EntityDamageByEntityEvent subclasses
- Fixed an NPE in the `mm m info` command
- Fixed shield colors not applying correctly
- Fixed some issues with VAULT provider
- Fixed several bugs with the speak mechanic
- Fixed `hit` mechanic multiplier not applying to secondary damage types
- Fixed bugs with takeItem mechanic
- Fixed undoPaste requiring a target
- Fixed incompatibilities with armorstand furniture closes #1396
- Fixed error with damagers in different worlds closes #1383
- Fixed NPE in ModifyScoreMechanic closes #1387
- Fixed UnsupportedOperationException in MobListener closes #1395
- Fixed some issues with Options.PreventCrafting and Options.PreventAnvil
- Fixed IllegalStateException in SetHealthMechanic
- Fixed title message options so they're now optional
- Fixed no such element in location targeter.
- Fixed NPE with PreventAnvil set to true.
- Fixed `hit` mechanic not working with onAttack mechanic
- Fixed `CRITICAL_STRIKE` stat not applying to bonus damage types
- Fixed villager trades being broken and some other related issues
- Fixed onAttack firing when event has been cancelled
- Fixed condition actions not working with TriggerConditions
- Fixed several errors with targeter audiences
- Fixed NPE with FlyingSpeed attribute
- Fixed bugs with custom player heads
- Fixed placeholders for mob type in `summon` mechanic 
- Add placeholder support to `distance` condition
- Fixed some villager trade bugs
- Fixed `targetSelf=true` not working with `@EntitiesInRadius` targeter 
- Fixed loading bug with triggerItemType condition
- Fixed potential loading issue with takeItem mechanic
- Fixed NPE when handling EntityMetadata packet
- Fixed hit mechanic not triggering onAttack 
- Fixed onDamaged mechanics firing even if event was cancelled
- Fixed Laser effect on 1.20.2 
- Fixed NPE in Mob bullet 
- Fixed some range issues with some packet bullets

Older Changelogs
================
-   [5.5.X Changelogs](/changelogs/5.5.x_changelogs)
-   [5.4.X Changelogs](/changelogs/5.4.x_changelogs)
-   [5.3.X Changelogs](/changelogs/5.3.x_changelogs)
-   [5.2.X Changelogs](/changelogs/5.2.x_changelogs)
-   [5.1.X Changelogs](/changelogs/5.1.x_changelogs)
-   [5.0.X Changelogs](/changelogs/5.0.x_changelogs)
-   [4.14.X Changelogs](/changelogs/4.14.x_changelogs)
-   [4.13.X Changelogs](/changelogs/4.13.x_changelogs)
-   [4.12.X Changelogs](/changelogs/4.12.x_changelogs)
-   [4.11.X Changelogs](/changelogs/4.11.x_changelogs)
-   [4.10.X Changelogs](/changelogs/4.10.x_changelogs)
-   [4.9.X Changelogs](/changelogs/4.9.x_changelogs)
-   [4.8.X Changelogs](/changelogs/4.8.x_changelogs)
-   [4.7.X Changelogs](/changelogs/4.7.x_changelogs)
-   [4.6.X Changelogs](/changelogs/4.6.x_changelogs)
-   [4.5.X Changelogs](/changelogs/4.5.x_changelogs)
-   [4.4.X Changelogs](/changelogs/4.4.x_changelogs)
-   [4.3.X Changelogs](/changelogs/4.3.x_changelogs)
-   [4.2.X Changelogs](/changelogs/4.2.x_changelogs)
-   [4.1.X Changelogs](/changelogs/4.1.x_changelogs)
-   [4.0.X Changelogs](/changelogs/4.0.x_changelogs)
-   [2.5.X Changelogs](/changelogs/2.5.x_changelogs)
-   [2.4.X Changelogs](/changelogs/2.4.x_changelogs)
-   [2.3.X Changelogs](/changelogs/2.3.x_changelogs)
-   [2.2.X Changelogs](/changelogs/2.2.x_changelogs)
-   [2.1.X Changelogs](/changelogs/2.1.x_changelogs)
-   [2.0.X Changelogs](/changelogs/2.0.x_changelogs)
-   [Pre-2.0 Changelogs](/changelogs/pre-2.0_changelogs)