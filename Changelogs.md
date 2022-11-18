5.2.0 (Development)
=====
General
-------
- Rewrote how mob data is saved
  - Mobs will now save all data using Persistent Data Containers, instead of just certain data
  - Mob data is no longer saved in a file at all
  - Optimized and fixed numerous errors with mob saving/loading 
- Rewrote Random Spawning system
  - Now always obeys mob caps and rules in spigot.yml
  - Fixed numerous bugs with random spawns
  - Reduced overhead by 80%
- Rewrote biome-related code
  - Everywhere biomes are supported now support custom biomes
  - Biomes use the same format as in the F3 menu, e.g. "minecraft:desert". Old biomes should translate over fine in most cases though.
  - Biomes can use wildcards to match multiple biomes. such as "minecraft:*swamp" to match mangrove swamps too
- Added <bar> placeholder
- Added `/mythicmobsmenu` or `/mmm` command (premium-only)
- Improved error messages and catching

Mobs
----
- Added missing option for frogs, `Options.Type: [WARM/COLD/TEMPERATE]`

Mechanics
---------
- Added `onCooldownSkill` option to meta-skills

### NEW: setSkillCooldown
- `- setSkillCooldown{skill=X;seconds=#}`

Conditions
---------
### NEW: chance
Finally added a regular chance condition
- `- chance{chance=1}`
- 1 = 100%
- Supports placeholders and math

### NEW: isFlying

### NEW: playersOnline
Matches number of players online
- `- playersOnline{amount=>5}`

### NEW: playersInWorld
Matches number of players in the current world
- `- playersInWorld{amount=>5}`

### NEW: skillOnCooldown
If a skill is on cooldown for the caster
- `skillOnCooldown{skill=X}`

Targeters
---------
- Added `blockCentered=true` option to all location targeters

Items
-----
- Added Template support for items
- Added `Group` option for grouping items into types
- Added corresponding group view to items GUI

Placeholders
---------
- Added more math operators: `>, >=, <, <=, ==`
- Variable add/sub mechanics now supports placeholders
- baseDamage mechanic now supports placeholders

### NEW: <bar>
- Special placeholder that generates a progress bar
- Can have other placeholders nes

### NEW: `<caster.skill.skill_name.cooldown>`

GUI
---
### NEW: Mob GUI
- Added a basic mob editor GUI (premium-only)
- This is only for quickly editing basic attributes of mobs such as health and damage. While this might be expanded on in time, there are no plans to fully replace config files with GUIs, especially not for anything involving skills.

Bug Fixes/Other
--------------
- Wearing condition can now check for AIR/empty armor slots.
- Fixed concurrency exception in @MIR targeter
- Fixed missing bossbar on non-despawning mobs after reload
- Fixed NPE in /mm egg give when using amounts.
- Fixed NPE in /mm m info command with invalid mob name.
- Fixed NPE in orbital mechanic bullets
- Fixed distance error in shoot mechanic
- Fixed error in distance mechanic
- Fixed NPE in projectile bullets involving worldguard
- Fixed NPE in summon mechanic
- Fixed command drops not running when killed by non-players
- Fixed NPE in mob spawning when other plugins despawn a mob 1 tick later
- Fixed onDamaged aura behaving oddly if ModelEngine isn't installed

5.1.4
=====
Mechanics
--------
### NEW: SetRaiderPatrolLeader
- Sets the raider patrol leader
- setRaiderPatrolLeader{leader=true} @target

### NEW: SetRaiderPatrolBlock
- Sets the target raider to patrol the given location
- setRaiderPatrolBlock @location

### Damaging Mechanics
- Fixed `ignoreEnchants` option
- Added `FREEZE` damage cause
- Fixed `preventKnockback` returning an unknown damager for some damage causes 
- Fixed `preventImmunity` option not working as intended

Conditions
---------
### NEW: isPatrolLeader
- Checks if the target entity is the captain of a pillager group

Bug Fixes/Other
--------------
- Fixed `preventStacking` item option
- Fixed AI pathing with openDoor, breakDoor, float and fleeSun AI goals
- Fixed the MythicHealMechanicEvent error being called async by making it only run when forced sync
- Fixed guardian beam effect on 1.19
- Fixed item attributes not working on spigot servers
- Fixed an issue in BukkitEntity#setCustomName if the server version is not supported
- Added `<caster.children.size>` placeholder which returns the amount of children the caster currently has
- Trying to fix some weird issues with onDamage aura

5.1.2
=====

General
-------
- Added 1.19.x support
- Added `CancelIfNoTargets: false` option for meta-skills, will continue executing the skill even if TargetConditions prune all
  possible targets.
- Added `Base: [level]`, `ScaleVanillaMobs: true`,`BelowZero: [modifier]` options for world level scaling

Mobs
---
- Added Options.FlyingSpeed for flying mobs
- Fixed some issues with attributes

Mechanics
--------
### NEW: ShowEntity
- Shows the hidden caster to the targeted players
- `- showEntity{} @NearestPlayer{r=10}`

### Auras
- Fixed doEndSkillOnTerminate=false not working

### Damaging Mechanics
- Fixed `ignoreenchants` spelling

Conditions
---------
### Altitude
- Improved altitude condition to work in the nether and underground
- MaxHeight option is now set to 30 by default

### BowTension
- Fixed an error with bowtension needing mythiclib methods

API
---
- Added MythicHealMechanicEvent
- Added several methods to Pack api
- Added a few methods to UUIDUtil, CompoundTag & CompoundTagBuilder

Bug Fixes/Other
---------------
- Updated to the latest adventure snapshot
- Improved Skill logging
- Fixed crashing caused by FillChest mechanic
- Added more support for some sculk particles
- Fixed BukkitEntity#getMaxHealth getting the incorrect value
- Fixed issues with stun mechanic
- Fixed NPE in distance condition
- Fixed NPE with mount mechanic


5.1.1
=====

General
-------
- Added raider-related options to Raider mob types

Mechanics
---------
### NEW: EndProjectile
- Terminates the projectile. Only usable in projectile mechanics.

### FillChest
- Can now target other containers, not just chests
- Added `shouldStack=true/false` option

### OnDamaged
- Fixed ondmg deflect not checking subhitbox

### ParticleLine
- Added maxdistance to particleline effect (defaults to 256)

### Projectile
- Added arrowType=NORMAL,SPECTRAL,TRIDENT to Projectiles
- Fixed projectile max duration
- Allow caster placeholders to be evaluated in projectile hit conditions

### TakeItem
- Can now target other containers instead of just player inventories

Conditions
----------
### HasItem
- Can also check other containers

API
---
- Added several methods to SkillConditions

Bug Fixes/Other
---------------
- Added <skill.var.interval> or <skill.var.itr> to mechanics using repeat & repeatInterval options
- Fixed NPE for MythicDungeons world unloading
- Fixed player not keeping same pitch/yaw when using teleport mechanic
- Allow string lists in item NBT section
- Added placeholder support to item attributes sections
- Fixed spawner RadiusY not saving
- Added Base level option to world scaling config
- Added placeholder support to custom skill parameters

5.1.0
=====

General
-------
- Added 1.19 support
- Added FROG, TADPOLE, and WARDEN mob types
- Added support for particles SCULK_SOUL, SHRIEK, SCULK_CHARGE, SCULK_CHARGE_POPS, and SONIC_BOOM
- Started on Item Editor GUI (premium-only)
- Added random(min,max) function to math parser
- Added more support for math and placeholders all over the place

Mechanics
---------
### NEW: SetTongueTarget
- Sets the tongue target for a frog caster to the target entity

### NEW: SetVariableLocation
- Sets a variable to the target location

### Damage
- Added `ignoreEnchants=true/false`

### SchematicPaste
- Will now read schematics from a Schematics folder in Packs

### Stun
- Added NoKnockback option

Conditions
----------
### NEW: HasAI
  - Tests if the target has AI

### NEW: isClimbing

Custom AI
---------
### NEW: MoveToWater
### NEW: MoveToBlock
- `moveToBlock{material=STONE;radius=8;radiusY=2;speed=0.9}`

### NEW: MoveToLava

API
-----
- Added some methods to BukkitAPIHelper
- Fixed NPE in MythicMobSpawnEvent#getMythicSpawner
- Fixed isFromMythicSpawner always returning false in MythicMobSpawnEvent

Bug Fixes/Other
---------------
- Fixed NPE when loading MythicItems
- Fixed NPE with owner mechanics/conditions
- Fixed cyclical dependency issues with ModelEngine and ProtocolLib
- Fixed a spawning errors with the api
- Fixed inaccurate skill cooldown
- Add "<#>" to be able to comment out lines on inline metaskills
- Fixed NPE in raytrace mechanics
- Fixed raytracing hitting the caster when using multi-hitbox
- Fixed cooldowns that are 1 second or less
- Fixed an NPE in ownerIsOnline condition
- Fixed an NPE when loading items
- Fixed issue with projectile onBounce
- Fixed OBB not working with OtherFactionGoal
- Fixed an NPE on some server forks
- Fixed projectiles on Mohist
- Fixed BlocksInChunk targeter not working on blocks below y=0
- Fixed RandomSpawns not always replacing vanilla mobs

5.0.4
=====

Mechanics
---------
### onDamaged Aura
Added deflectProjectiles and deflectConditions options to onDamaged aura

Conditions
----------
### NEW: BowTension Condition

Triggers
--------
- Added ~onBreed trigger
- Added ~onPress trigger (Requires MythicKeys)
- Added ~onRelease trigger (Requires MythicKeys)

Targeters
---------
- Added limit,sort options for location targeters

### NEW: @Mom and @Dad
- Targets parents when mob was bred

### @Forward
- Added lockpitch=true option

### @TargetLocation
- Updated @TargetLocation to use raytracing for players to be more accurate

Custom AI
---------
- Added breed goal for animals

Bug Fixes/Other
---------------
- Readded `Options.AppendType: false` option for items
- Placeholder support for horizontalradius in Projectile/totem/missile
- Fixed crashing issue with mob types that no longer exist
- Fixed several major compatibility issues
- Fixed NPE in boss bars
- Fixed orbital bullets spawning at the center point
- Fixed speedModifier to several AI goals and goto mechanic
- Fixed BlockWave not working on 1.18.2
- Fixed color code issues
- Fixed some placeholder NPEs
- Fixed message formatting
- Fixed some blackmask effect issues
- Fixed vanilla mobs not working with spawn command
- Fixed WorldGuard support not considering “block-plugin-spawning: false”
- Fixed NPE with new model system
- Fix mutators not working on @TriggerLocation
- Fixed display issues with item drop type
- Fixed Model Engine Sub-hitbox compatibility
- Fixed yRadius in BlocksNearOriginTargeter
- Fixed placeholders not parsing correctly in varequals
- Fixed some issues with GoToLocation AI goal
- Fixed RandomSpawns affecting vanilla mob spawning rate
- Fixed bug with HolographicDisplays support
- Fixed lag issues from ProtocolLib/ removed PL features since they aren't really relevant anymore
- Fixed &r
- Fixed shields always having a banner
- Fixed placeholders in skill cooldowns
- Fixed NPE with mob spawners
- Fixed mobs doing damage even if damage is set to 0
- Fixed oxygen mechanic running async
- Fixed taming mobs with Options.Tameable: false set
- Fixed trigger not passing in onAttack aura
- Fixed trigger not passing in onDamaged aura

5.0.2
=====
Bug Fixes/Other
- Fixed several major compatibility issues

5.0.1 (Beta Build)
======

Highlights
----------
- Now requires Java 16
- Mythic API being separated out into an independent module (for add-on authors)
- Major API rewrite
- Registering custom triggers
- Native model configuration for ModelEngine
- MythicKeys mod support

General
-------

### Model Configuration
You can now configure ModelEngine models inside your mob.

```
Mob:
  Model: [model id]
```
or with more options...
```
Mob:
  Model:
    Id: [model id]
    ViewRadius: 64
    Drive: true
    DamageTint: true
```
etc...

Conditions
----------
### NEW: isFrozen
- Tests if the targeted entity is frozen

Targeters
---------

Mechanics
---------
### NEW: onKeyPress
- Requires [MythicKeys mod](https://github.com/ASangarin/MythicKeys) for the client and [MythicKeysPlugin](https://www.spigotmc.org/resources/mythickeysplugin-custom-keybinds-api.98893/) for the server.
- Applies an aura to the targeted player and triggers a skill when the targeted player presses a key 
  - `onKeyPress{key=minecraft:server;onPress=metaSkillHere}`

### NEW: onKeyRelease
- Requires [MythicKeys mod](https://github.com/ASangarin/MythicKeys) for the client and [MythicKeysPlugin](https://www.spigotmc.org/resources/mythickeysplugin-custom-keybinds-api.98893/) for the server.
- Applies an aura to the targeted player and triggers a skill when the targeted player releases a key 
  - `onKeyRelease{key=minecraft:server;onRelease=metaSkillHere}`

### NEW: ShieldBreak
- Breaks the target player's shield block and disables their shield for `duration` ticks.

### PasteSchematic
- Changed fawePaste to PasteSchematic, now works with regular WorldEdit
- Added rotation=90/180/-90 to fawepaste mechanic

Bug Fixes/Other
--------
- Fixed mob drops on non-paper spigot
- Fixed onHitSkill for shoot mechanic not inheriting skill variables, closes #687
- Added `min(x, y)`, `max(x, y)`, `atan2(y, x)` math functions. You can see all the supported operators and functions in [Math](Skills/Math), and you can make suggestions to add more operators and functions to [gitlab](https://git.mythiccraft.io/mythiccraft/MythicMobs/-/issues)
- Fixed several mob AIs. closes #681
- Fixed NPE with WorldGuard support
- Fixed disguises sometimes not disappearing on mob removal

4.14.2
======
Commands
--------
- Made reload command sync again for now, added -a flag to make it async

Mechanics
---------
### NEW: GoTo

### NEW: onJump
- Applies an aura to the targeted entity and triggers a skill when the entity jumps

### NEW: onSwing
- Applies an aura to the targeted player and triggers a skill when the player swings/left clicks

### NEW: onInteract
- Applies an aura to the targeted entity and triggers a skill if the entity is interacted with.

Conditions
----------
### NEW: Charged
- True if a creeper is charged

### NEW: Plugin
- plugin{p=XXXXXX}
- Returns true if the specified plugin is running on the server

### NEW: Premium condition
- Returns true if Mythic Premium is running

Bug Fixes/Other
--------
- Added several `Targeter` default options in config.yml
- Added missing `FALLING_SPORE_BLOSSOM` and `SPORE_BLOSSOM_AIR` particles
- Changed `os` to `osh` for onshoot aura option
- Updated to support latest MythicLib
- Double-check that chunk is actually loaded when EntitiesLoadEvent fires
- Fixed an issue with MythicMobs trying to remove players
- Fixed setowner and removeowner modifying mob health
- Fixed an issue with randomspawner disabling MM if a biome is not valid.
- Fixed maxdistance attribute in shoot mechanic and also added placeholder support to it
- Fixed an issue with giveitem mechanic
- Fixed NPE in summon mechanic
- Fixed blocktype condition not checking for two or more block types.
- Fixed NPE in equip mechanic
- Fixed NPE in mob manager
- Fixed PlayersInRadius condition being wildly inaccurate on distance
- Fixed to return 'undefined' instead of null for unset string variables
- Fixed DynamicTrades for villagers not loading without any regular trades

4.14.1
======
API
---
- Added MythicMobInteractEvent

Bug Fixes/Other
--------
- Fixed placeholders parsing as math if decimals don't start with 0
- Improved tracking of vanilla types
- Fixed reloading error with some conditions
- 

4.14.0
======

**Highlights**
----------
- Added 1.18.1 support
- Bouncy projectiles
- A few bug fixes

General
-------
- Added 1.18.1 support
- Changed reload command to run async

Mechanics
---------
### Projectile
- Added **hugLiquid=true** option - when using hugSurface will also move on top of liquids.
- Added **bounce=true** option (premium-only)
- Added **bounceVelocityMod** option (defaults to 0.9)

Adding **bounce=true** will cause projectiles to bounce off of surfaces instead of just stopping. Every time it bounces, its velocity will be multiplied by _bounceVelocityMod_.

**The bounding box used for bouncing is calculated using the projectile's hit radius options, so if the projectile seems to be bouncing when it isn't close to a surface and you want more accuracy, try lowering the hit-radius!**

Calculating the physics for bouncing is quite intensive, so don't go too crazy with it on weaker servers!

### NEW: ConsumeSlot
- removes any item in the specified slot of the player's inventory.
  - `consumeslot{slot=25;amount=21} @PlayersInRadius{r=10}`
  - `consumeslot{slot=HAND;amount=21} @PlayersInRadius{r=10}`

### NEW: PickUpItem

### NEW: StopSound
- effect:stopsound{sound=ambient.cave;soundcategory=master} @target
- Stops a specific sound from being played to the targeted player.

### NEW: onDeath
- Added onDeath aura. Treat it as if it was ~onDeath trigger and not use any targeters that will target the entity that died.

### NEW: onBlockPlace
- Aura that fires when the target places a block.

### NEW: TakeItem
- removes a certain amount of items from the player's inventory.
  - `- takeitem{i=myTestItem;amount=20} @PlayersInRadius{r=10}`

### Delay
- Added placeholder support

### Firework
- Completely rewritten and fixed

### ItemSpray
- Allow drop tables for itemSpray effect (will use random items from it)

### RandomSkill
- is now weighted.
- skill weight defaults to 1 if not specified
- randomskill will not select a skill with weight of 0.
- Here are a few examples: 
  - `- randomskill{skills=metaskill 95,otherskill 4,someskill 0,testskill}`
  - `- randomskill{skills=metaskill 200,otherskill 0.25,someskill 55.23,testskill}`

### SendTitle
- Can use hex colors

Targeters
--------

### NEW: RingAroundOrigin
- Targets points in a ring around the skill origin
- Aliases: `RAO`
  - `@ringaroundorigin{radius=#;points=#}`
  
### NEW: RandomLocationsNearOrigin
- Targets random locations near the skill origin
- Aliases: `RLO`, `randomLocationsOrigin`, `RLNO`
  - `@randomlocationsnearorigin{amount=#;radius=#;minr=#;spacing=#}`

### NEW: RandomLocationsNearCaster
- Targets random locations near the skill caster
- Aliases: `RandomLocations`, `RL`
  - `@randomlocationsnearcaster{amount=#;radius=#;minr=#;spacing=#}`

### TargetLocation
- Added maxDistance option (defaults to 30 blocks)

### Ring Targeter
- Added rotZ, rotY, rotZ options to rotate the ring
  
Conditions
--------

### NEW: ItemIsSimilar
- Tests if the item from the specified slot is similar to the item being compared
  - `- itemissimilar{i=myTestItem;slot=25} true`
  - `- itemissimilar{i=myTestItem;slot=CHEST} true`

### NEW: EntityItemIsSimilar
- Tests if the item entity's ItemStack is similar to the item being compared
  - `- entityitemissimilar{i=myTestItem} true`

### NEW: EntityItemType
- Tests the item type of the target item entity, will check the item's custom model data.
  - `- entityitemtype{types=diamond} true`

### NEW: EntityMaterialType
- Tests the material type of the target item entity
  - `- entitymaterialtype{types=diamond} true`

Entity Types
--------
### NEW: ITEM

Placeholders
--------
- Added `<random.float.#to#>` which returns a random floating point number in a specified range
- Added `<target.held.item>` and `<trigger.held.item>`
- Added `<caster.display>`

Random Spawns
-------------
- Added Cooldown option for random spawners (in seconds)

Bug Fixes/Other
---------------
- Fixed FillChest mechanic only filling chests with vanilla items
- Allow ~onSignal to trigger multiple skills with the same signal ID
- Fixed SpawnMob command spawning the base mob instead of the overridden vanilla mob if there's any in the VanillaMobs.yml
- Show droptables in get/give command
- Fixed NPE in orbitals when using MOB as the bullet type
- Fixed command drops executing only one command
- Fixed MobsInRadius condition not working in RandomSpawns
- Fixed targeting issues with auras
- Fixed `Options.PreventSlimeSplit`
- Fixed precision issue with VariableAdd and VariableSubtract (#531)
- Fixed PlayerWithin-type conditions to ignore creative/spectator players
- Fixed an issue with inline skills/conditions needing space before `]`

Older Changelogs
================
-   [5.1.X Changelogs](/5.1.x_changelogs)
-   [5.0.X Changelogs](/5.0.x_changelogs)
-   [4.13.X Changelogs](/4.13.x_changelogs)
-   [4.12.X Changelogs](/4.12.x_changelogs)
-   [4.11.X Changelogs](/4.11.x_changelogs)
-   [4.10.X Changelogs](/4.10.x_changelogs)
-   [4.9.X Changelogs](/4.9.x_changelogs)
-   [4.8.X Changelogs](/4.8.x_changelogs)
-   [4.7.X Changelogs](/4.7.x_changelogs)
-   [4.6.X Changelogs](/4.6.x_changelogs)
-   [4.5.X Changelogs](/4.5.x_changelogs)
-   [4.4.X Changelogs](/4.4.x_changelogs)
-   [4.3.X Changelogs](/4.3.x_changelogs)
-   [4.2.X Changelogs](/4.2.x_changelogs)
-   [4.1.X Changelogs](/4.1.x_changelogs)
-   [4.0.X Changelogs](/4.0.x_changelogs)
-   [2.5.X Changelogs](/2.5.x_changelogs)
-   [2.4.X Changelogs](/2.4.x_changelogs)
-   [2.3.X Changelogs](/2.3.x_changelogs)
-   [2.2.X Changelogs](/2.2.x_changelogs)
-   [2.1.X Changelogs](/2.1.x_changelogs)
-   [2.0.X Changelogs](/2.0.x_changelogs)
-   [Pre-2.0 Changelogs](/pre-2.0_changelogs)}