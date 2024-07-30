[[_TOC_]]

# 5.7.0

## General
- Added 1.20.5, 1.20.6 and 1.21 support
- Dropped support for 1.16.4, 1.18.2, 1.19.1, 1.19.2, and 1.19.3.
- Various options on mobs and skills that take an item can now accept a droptable and will use a random item from it, such as the Item mob type.

## Mobs
- Added support for new entity types: `Armadillo`, `Bogged`, and `Breeze`.
- Added new HEARING ability to mobs enabled by `Hearing.Enabled: true`. Requires 1.20+
- Added [`~onHear`](/Mobs/Mobs#hearing) trigger that responds to hearing sounds
- Added `Options.PreventConversion` to zombies and skeletons.
- Changed variables defined directly on the mob default to always saving.

## Skills
### Mechanics
- Added particles: `white_smoke`, `dust_plume`, `gust`, `gust_emitter`, `gust_dust`, and `trial_spawner_detection`
- Particle `mobSpellAmbient` was removed by Mojang in 1.21
- Allow `command` and `message` mechanics to target locations for the purpose of location-based placeholders.
- Renamed `setItemDisplay` mechanic to `setDisplayEntityItem` to clarify purpose and avoid naming conflicts.

#### NEW: `Log`
- `log{message="Debug to console with variables <caster.var.test>"}`

#### NEW: `SetTextDisplay`
- `setTextDisplay{text="text here"} @Target`

#### NEW: `Taunt`
- Sets the caster's threat to 110% of the current target's target and forces them to attack the caster. Requires threat tables.

#### NEW: `openTrades`
- `openTrades (openTrade, trade)` mechanic to open a merchant menu to the targeted player.
- Added `realTrade/real` attribute - determines if the player trades with the actual villager or not (ie drop trade xp, etc.).

#### NEW: `setChunkForceLoaded`
- Sets the target location's chunk to be force-loaded

#### DropItem
- Added `then=` skill to the dropItem mechanic that targets the dropped item entities.

### Conditions
- Added `onPass[Skill]` & `onFail[Skill]` for conditions.

#### NEW: `boundingBoxesOverlap`

#### NEW: `distanceFromPin`
- `distanceFromPin{pin=X;distance=<5}`

#### NEW: `distanceFromLocation`
- `distanceFromLocation` condition. Values `x`,`y`,`z`,`distance/d`, and optional `world` (default to players current world if no world name provided).

### Targeters
#### NEW: `@BlocksInPinRegion`

#### NEW: `@HighestBlock`
- Targets the highest location at the origin position.

#### NEW: `@TrackedPlayers`
- Targets players that are within render distance of and currently rendering the mob

#### NEW: `@ChunksinWERegion`
- Added `@ChunksinWERegion{region=X}` targeter.

#### Pin
- Added `random=true` option, if targeting a multi-pin it will target a random one instead of all of them.

### Placeholders
- Added `PlaceholderBoolean` which will evaluate to true if a variable is 'true' or '1', otherwise false.
- Added rounding support to `random.float` placeholder by using syntax `<random.float.1to5{round=2}>`

API
----
- Refactored EquipSlots to allow for custom slots.
- Various API improvements for MythicRPG.
- Added methods for dumping item component data.

Bugs / Other
------------
- Improved world isLoaded check.
- Removed `type` alias for `damageType` in damage mechanics to fix some conflicts.
- Removed adventure shading, switched to using native adventure with spigot libraries loader.
- Removed redundant old version checks.
- Fixed bugs with rounding in stat tooltips in some cases.
- Fixed y out of range error with random spawning.
- Fixed setName mechanic not updating properly when using custom nameplates.
- Fixed NPE in papi variable placeholders.
- Fixed several NPEs when trying to resolve player variables before a player has finished loading in.
- Fixed several more bugs with placeholder rounding.
- Fixed attribute slots not working on some versions.
- Fixed colors not working in stat formatting.
- Fixed async error with threat table targeters.
- Fixed NoSuchElementException leading to server crash with random spawning on 1.21.
- Fixed NPE in dumpNBTData method on 1.21.
- Fixed `Spawners.DisableCommandSaving` logic being backwards.
- Fixed yaw and pitch attributes not saving on spawners.
- Fixed spawners not saving.
- Fixed a bunch of broken targeters.
- Fixed NPE in VariableManager.
- Fixed attack speed stat (hopefully).
- Fixed spread not working on teleport mechanic with entity targets.
- Fixed bug with item display entities.
- Fixed backwards compatibility with potions.
- Fixed Armor and Attack Speed not being able to be set to 0.
- Fixed errors related to EntityManager.
- Fixed a bunch of spam errors about registering entities.
- Fixed NPE with mob eggs that have no display name.
- Fixed piglin brutes being broken for vanilla overrides.
- Fixed some other vanilla override issues with babies.
- Fixed totem_of_undying particle.
- Fixed a bunch of particle bugs.
- Fixed default potion level being 2 instead of 1.
- Fixed fireworks loading colors with RBG instead of RGB.
- Fixed onDamaged aura not working with skill damage, probably.
- Fixed ClassCastException with compatibility mode.
- Fixed NPE with `targetInterval` mechanic option.
- Fixed spread not working on teleport mechanic with entity targets.
- Fixed summon mechanic mobs inheriting caster's yaw in certain situations.
- Fixed `hasPotionEffect` condition on 1.21.
- Fixed custom attribute registration on 1.21+.
- Fixed async error with threat table targeters.
- Fixed NoSuchElementException leading to server crash with random spawning on 1.21.
- Fixed custom attribute registration on 1.21+.
- Fixed y out of range error with random spawning.
- Fixed summon mechanic mobs inheriting caster's yaw in certain situations.
- Fixed piglin brutes being broken for vanilla overrides.
- Fixed some other vanilla override issues with babies.
- Fixed default potion level being 2 instead of 1.
- Fixed fireworks loading colors with RBG instead of RGB.
- Fixed onDamaged aura not working with skill damage, probably.
- Fixed summon mechanic mobs inheriting caster's yaw in certain situations.
- Fixed `hasPotionEffect` condition on 1.21.
- Fixed custom attribute registration on 1.21+.
- Fixed spread not working on teleport mechanic with entity targets.
- Fixed `setName` mechanic not updating properly when using custom nameplates.

5.6.2
=====

Random Spawning
---------------
- Rewrote the random spawning generator and added some new config options
- Added `ReplaceObeysCap` to random spawning, defaulting to false.

Bugs / Other
------------
- Added `onSummon` (alias `then`) attribute to `summon` mechanic, if specified will run the skill on the summoned mob after it's summoned.
- Added `<caster/target/trigger.raytrace.#>` placeholder
- Added `<target/trigger.stat.STAT_NAME>` placeholder
- Added `DisplayOptions.TeleportDuration` option
- Added `Options.VisibleByDefault`
- Added `executeAfterDeath=true` option to `skill` and `vskill` mechanics
- Added `fakelightning` and `fakeexplosion` aliases for those effect mechanics
- Added `fromOrigin` to fireball mechanic
- Added `inheritDespawnOption` option to summon mechanic
- Added placeholder support to `limit` targeter option
- Added placeholder support to WEPasteSchematicMechanic `x/y/z` offsets and `rotation` options
- Added sub-hitbox deep active mob parent search
- Attempt to catch errors in command mech to prevent npc breakage
- Changed `permanent` option in hide mechanic to `ignoreAuraOptions`
- Fixed spawner data sometimes getting wiped during reloads
- Fixed GlowEffect auras not merging correctly
- Fixed GlowEffect NPE
- Fixed IllegalArgumentException in cluster spawning generator
- Fixed NPE in Fireball mechanic closes #1561
- Fixed NPE with invalid skill parameters
- Fixed NPE with new random spawn generator
- Fixed NPEs in GlowManager
- Fixed NoSuchMethodError when spawning mobs
- Fixed StackOverflowError caused by mob recursively damaging itself closes #1546
- Fixed block light and sky light display options
- Fixed error with EnderDragonAlive condition used with random spawns closes #1539
- Fixed extremely rare race condition with mobs despawning the same tick they die
- Fixed IllegalArgumentException in cluster spawning generator
- Fixed mobs with no display name set having a display name
- Fixed non-mob entities throwing an error with PreventOtherDrops
- Fixed pin wand being able to break blocks
- Fixed potion clear mechanic not clearing all potion effects when not providing any type.
- Fixed some bugs with the Biomes field in random spawners closes #1558
- Fixed some more issues with multi-hitbox support
- Fixed `repeat=X` not working if repeatInterval is 0 closes #1555
- Fixed scope.raytrace placeholders
- Fixed bugs with rally mechanic
- Removed a cancelDamage alias

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

Older Changelogs
================
-   [5.7.X Changelogs](/changelogs/5.7.x_changelogs)
-   [5.6.X Changelogs](/changelogs/5.6.x_changelogs)
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