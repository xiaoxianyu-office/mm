5.4.0 (Dev Builds)
=====

General
-------
- Added `/mm test mechanic [line]` command to test executing a skill line

Mobs
----
Added new mobs types:
- `BLOCK_DISPLAY`
- `CAMEL`
- `CHEST_BOAT`
- `ITEM_DISPLAY`
- `SNIFFER`
- `TEXT_DISPLAY`

Mechanics
----------

### NEW: SetTransformation
- Transforms the target display entity
```yml
- transformation{action=set;transformation=translation;value=0,0,1} @self

- transformation{action=set;transformation=right_rotation;value=0,0,0,1} @self ~onwhatever
```
Action valuees: SET, ADD, MULTIPLY, DIVIDE
Transformation values: TRANSLATION, SCALE, RIGHT_ROTATION, LEFT_ROTATION

### NEW: `setProjectileDirection`
- Changes calling projectile's direction to the given target

### Damage Mechanics
- Added `ignoreShield`, `ignoreEffects`, `ignoreResistance`, `damagesHelmet`, and `noAnger` boolean options to damaging mechanics

### Particle Effects
- Added new particles: DRIPPING_CHERRY_LEAVES, FALLING_CHERRY_LEAVES, LANDING_CHERRY_LEAVES

### Projectile Mechanics (Projectile, Missile, etc)
- Added `tickInterpolation` option (defaults to 0)

Setting tickInterpolation will interpolate that many points between each tick in a projectile and execute the onTick and onHit skills on those points as well, doing multiple 'ticks' in a single tick.

This can be used to fill in the gaps with super-fast projectiles and also prevent entities from being skipped over by insanely fast projectiles.

- Added `interactable=true`, `onInteractSkill` to projectiles (requires 1.19.4+), used to allow the player to hit the projectile similar to a ghast fireball.

### Missile
- Added `hugSurface` and `bounce` options to missile mechanic (and all other related options similar to the Projectile mechanic)

### Lunge
- Added `oldMath/old/o` attribute to determine if it should use the old wonky math (default: false)

5.3.1+
======

General
-------
- Added bulletForwardOffset to projectile bullets, defaults to 2.5
- Added `bulletOffset` option for bullets (defaults to 1.8)

Bugs / Other
------------
- Added placeholder support to teleport mechanic
- Fixed loading issue on 1.18
- Fixed NPE in DamagingMechanics
- Fixed passthrough damage not including modifier damage
- Fixed error with strEquals condition when using caster placeholders closes #1185
- Fixed blockType and blockIgnore targeter filters not working unless a limit is set closes #1182
- Fixed ThreatTables targeting same-faction players
- Fixed `setVariableLocation` mechanic not working with non-entity targets
- Fixed nonsensical error in onDamaged aura
- Fixed hugSurface projectiles being broken with highAccuracy enabled
- Fixed blockmask being broken
- Fixed placeholder support in score mechanic 
- Fixed suicide mechanic not working with PassthroughDamage enabled
- Fixed PassthroughDamage not working with certain damage types
- Fixed several issues with asParent, asOwner, asTrigger target modifiers
- Fixed memory leak with certain aura configurations

5.3.0 (The Pande Update)
=====
Highlights
----------
### Version support
Added support for 1.20.1

Dropped support for the following versions
- 1.12
- 1.17
- 1.18.0
- 1.19.0
- 1.19.1

### Composite Conditions
Added composite conditions. Conditions in a skill can now be grouped with parenthesis and combined with AND (&&) and OR (||) operators, and can also be nested for complex logic. The entire group of conditions will be evaluated together.
```
Conditions:
- ((night || raining) && onBlock{material=LIME_CONCRETE}) true
```

### Projectiles
- Added `DISPLAY` and `TEXT` bullets
- Most bullets are now packet-based
- Added lots of new projectile options and mechanics

### Tons of new Random Features
- Lots of new random features and mechanics added by Pande. Go thank him!

General
-------
- Improved tab completion for most commands

Mobs
---------

### New Attributes
- Added [ReviveHealth](/wikis/Mobs/Options#revivehealth) option
- FollowRange can now be zero

### Templates
- Templates have been fixed and refactored, and now a [Wiki Page](/Mobs/Templates) has been created to made you aware of their existance at all

Mechanics
----------
### NEW: [UndoPaste](/skills/mechanics/undopaste)
### NEW: [Slash](/skills/mechanics/slash)
### NEW: [Saddle](/skills/mechanics/saddle)
### NEW: [ProjectileVelocity](/skills/mechanics/projectileVelocity)
### NEW: [Polygon](/skills/mechanics/Polygon)
### NEW: [SetDragonPodium](/skills/mechanics/SetDragonPodium)
### NEW: [Time](/skills/mechanics/time)
### NEW: [Attribute](/skills/mechanics/Attribute)
### NEW: [AttributeModifier](/skills/mechanics/AttributeModifier)
### NEW: [AddTrade](/skills/mechanics/AddTrade)

+ Add addTrade mechanic; aliases: setTrade, removeTrade, "replaceTrade

Attributes:
- action | mode | m - What to do <ADD>
- slot | s | index - The slot to be selected for actions <0>
- ingredient | item | ingredient1 | item1 | i | i1 - The first ingredient <STONE>
- ingredient2 | item2 | i2 - The second ingredient <null>
- result | r - The result item <STONE>
- maxUses | uses | u - The uses of the trade <Max Int>
- experienceReward | expReward | exp | dropExp - If the trade should drop experience <false>
- priceMultiplier | multiplier - The multiplier for the price when the player has made the villager angry <0>
- demand | d - The demand of the trade <1>
- specialPrice | special - The special price for when the villager is friendly to the player (player reputation or hero of the village effect) <1>
- ignoreDiscounts | discounts - If the discounts should be ignored <false>

### FawePaste
- added `id` attribute, to use in concert with UndoPaste
- it now *truly* runs async
### Lunge
- fixed the vy attribute
### ModifyProjectile 
- added the `ADD` action
### Projectile

- Added `DISPLAY` and `TEXT` bullet types
  - Text Bullets: `- projectile{bullet=TEXT;bulletText="...";bulletBillboard=CENTER;backgroundColor=64,0,0,0}`

- Allow 3D rotations for ArmorStand & Display projectiles:
  - pitch - The pitch rotation <0>
  - yaw - The yaw rotation <0>
  - roll - The roll rotation <0>
  - rotation | rot - The rotation of the polygon, in the x,y,z format <0,0,0> (compact form for pitch/yaw/roll)
  - pitchSpeed|ps & yawSpeed|ys & rollSpeed|rs & rotationSpeed|rots, same as previous, but to add speed to the rotation

- Added option `highAccuracyMode=[true/false]` - If true causes the projectile to use raytracing to determine if it will hit a block instead of regular checking, so that very fast projectiles wont clip through blocks.
- Added option `requireLineOfSight=[true/false]` - If true the projectile will immediately hit anything blocking line-of-sight from the projectile's origin to its 'starting point' after options are applied
- Added option `drawHitbox=true` - draws the entity-detection hitbox of the projectile around it in particles. Useful for making adjustments.
- Add option `bulletEnchanted`/`enchanted` to all armorstand/item display/item bullets

### Shoot
- fixed `pickup` attribute
- added `expiration` attribute
- added `amount` attribute
### SetBlockType
- added `physics` attribute
### Velocity
- added `relative` attribute
### Aura
- fixed `cancelOnChangeWorld` attribute
- added placeholder support for auranames
### OnBlockBreak 
- added `dropitem` attribute
- added `blocktype` attribute



Targeters
---------
- Added `ofOwner`,`ofParent` and `ofTrigger` attributes to all targeters. They will make the targeter be parsed by either the Owner, Parent or Trigger
- Fixed `samefaction=false` target filter

### NEW: [Rectangle](/Skills/Targeters/Rectangle)
### NEW: [BlockVein](/Skills/Targeters/BlockVein)
### EntitiesInCone
- fixed it targeting items

Triggers
--------
### NEW: [onBucket](/Skills/Triggers#onbucket)

### onDeath
- Paper Only: the event is now cancellable
- When the death event is cancelled, the mob will regain health in accordance with its ReviveHealth option

Conditions
----------
### NEW: [isMythicMob](/skills/conditions/ismythicmob)
### NEW: [isSaddled](/skills/conditions/isSaddled)
### NEW: [MythicPack](/skills/conditions/MythicPack)
### NEW: [PackVersion](/skills/conditions/PackVersion)
### NEW: [PackVersionGreater](/skills/conditions/PackVersionGreater)
### NEW: [ServerNMS](/skills/conditions/servernmsversion)
### NEW: [ServerVersion](/skills/conditions/ServerVersion)
### NEW: [Moist](/skills/conditions/moist)
### NEW: [Moisturelevel](/skills/conditions/moisturelevel)
### NEW: [isTamed](/skills/conditions/istamed)

Items
-----
### NEW: [CanPlaceOn](/Items/Items#canplaceon) item configuration
### NEW: [CanBreak](/Items/Items#canbreak) item configuration

Placeholders
------------
### NEW: Raycast placeholder
- <caster.raycast>
- <target.raycast>
- <trigger.raycast>
- <parent.raycast>
### NEW: PlaceholderAPI supoort
- %mythic_var_someVar%
- %mythic_var_world_someVar%
- %mythic_var_global_someVar%
- %mythic_var_<playerName>_someVar%
- %mythic_var_<uuid>_someVar%
### NEW: <parent.l.pitch>
### NEW: <parent.l.yaw>


Bug Fixes/Other
---------------
- Now the plugins looks for WE schematics even in FAWE/WE folders
- Fixed metaskills inline comments (`<#>`)
- added the Icon element in the packinfo configuration
- Fix for memory leak involving RandomFloat and RandomInt
- Fix iterator error with the Bucket trigger
- Added onHitBlockSkill for projectiles (projectile, missile, shoot...)
- Added Placeholder support for Score and ScoreGlobal conditions
- Fixes for raytracing
- Several fixes for spawner loading
- Fixed random number serialization
- Refactored mmo plugin support
- Added `Configuration.LoadExampleConfigs` (defaults to true) in config.yml
- Fixed several issues with Damage mechanic
- Rewrote projectiles to be packet based
- Added error catching when trying to load an entity with a mob type that doesn't match
- Fixed default stance when loading a mob from PDC
- Fixed NPE with samefaction target filter
- Improved tab completion for most commands
- Implemented stat api support for mobs
- Fixed blockmask error when MythicDungeons world unloads
- Fixes for samefaction target filter closes
- Fixed PreventMounts and PreventSplitting options
- Added "TEXT" bulletType for projectiles
- Add "bulletEnchanted"/"enchanted" to all armorstand/item display/item bullets
- Run blockIgnores/blockTypes filter before sorters for location targeters



5.2.6
=====
Bug Fixes/Other
---------------
- Fixed world scaling starting a level higher then intended
- Fixed errors with lunge mechanic
- Fixed non-despawning mobs forgetting their spawner
- Fixed dropitem mechanic passing the caster as the trigger instead of the trigger
- Fixed errors with NoDamageTicks
- Fixed death messages on 1.19.4
- Fixed world scaling bonuses starting at 1 instead of 0
- Fixed villager trades missing enchants
- Fixed ignore=samefaction target filter when used on players

5.2.5
=====
General
-------
- Added 1.19.4 support

Mechanics
---------

### NEW: StopUsingItem

### FillChest
- Add "shouldempty"/"empty" to fillChest to empty the chest before adding items

### onDamaged
- Allow placeholders in onDamaged aura damage mods

### Paste
- Added `blocksPerTick` option to paste mechanic

Conditions
----------
### NEW: isBaby

Triggers
--------
### NEW: onTrade

Items
-----
Allow listing the operation on item attributes after the number.

Supports number or names of operations.

  Examples:
  - `Damage: 20 ADD`
  - `Damage: 40 2`
  - `MovementSpeed: 200 MULTIPLY_BASE`

API
---
- Added `MythicMobPreSpawnEvent` called before a mob is actually spawned at all.

Compatibility
-------------
### CrashClaim
- Added support for CrashClaim to inClaim, nearClaim conditions

Bug Fixes/Other
---------------
- Make placeholders pass caster to papi if caster is a player and entity targets are not applicable
- Fixes for parent/child targeters
- Fixed raytrace fluidcollisionmode option not working
- Fixed NoClassDefFoundError when dispensing a mob egg from a dispenser
- Fixed yRadius, other issues with sphere shape in block targeters
- Fixed async error in fillChest mechanic
- Fixed NPE in OnDamaged mechanic introduced recently
- Fixed mobs forgetting who their parents are after chunk reload closes #1077
- Fixed non-despawning mobs healing on chunk reload
- Fixed armorstand mobs dying twice from TNT because of a spigot bug
- Fixed more placeholder issues with BlockMask effect
- Fixed "java.lang.NoSuchFieldError: bukkitChunk" error
- Fixed inconsistencies with MythicMobItemGenerateEvent
- Fixed blockmask placeholder not updating

5.2.3
=====
General
-------
- Added 1.19.3 support

Bug Fixes/Other
--------------
- Added support for Crucible custom blocks everywhere in skills
- Added offsets for SpawnLocationTargeter, CasterSpawnLocationTargeter, and TrackedLocationTargeter
- Added bounce error catching to projectile mechanic for pineapple
- Added placeholder support for blockmask effect material
- Fixed item version NBT being applied even when system isn't used
- Fixed runAIGoalSelector failing when using goals with options maybe
- Fixed blockwave effect being sent to players in other worlds
- Fixed a memory leak with placeholders and certain item options
- Fixed item version NBT being applied even when system isn't used
- Fixed runAIGoalSelector failing when using goals with options maybe
- Fixed blockwave effect being sent to players in other worlds
- Fixed NoSuchMethodError on regular spigot
- Fixed a few issues with mob and item loading
- Fixed plugin not loading if you have thousands and thousands of items
- Fixed IllegalArgumentException in Chain mechanic
- Fixed name condition not working in most cases
- Fixing more possible obscure memory leak issues with placeholders
- Fixed several issues with the EntitiesInCone targeter
- Fixed async error in look mechanic closes
- Fixed some bugs with holding and wearing conditions
- Fixed positioning of mob and item bullets to be more accurate with projectile mechanic
- Fixed error with item bullets on projectiles with zero velocity
- Fixed certain options that allow lists to not split by commas in-between brackets

5.2.0
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

### NEW: setTarget
- Sets the mob's target to the target entity
- If using threat tables, will increase threat to the threshold to change targets for the targeted entity

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

### NEW: structure
- Matches if the location is located inside of a structure
- `structure{s=minecraft:desert_pyramid}`
- Supports structures from datapacks

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

Compatibility
-------------
- `inClaim` and `nearClaim` conditions now support the Lands plugin

Bug Fixes/Other
--------------
- Added missing wildcard support to some spawner commands
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
- Fixed cuboid condition not supporting location targeters closes
- Fixed ignore=owner target filter not working
- Fixed itemSpray effect despawning too fast on some servers
- Fixed spawn egg dupe with dispensers
- Fixed fly mechanic targeting caster instead of target
- Fixed heal mechanics running async
- Fixed some NPEs in the error logger
- Fixed IllegalArgumentException in Distance condition
- Fixed various other bugs

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
-   [5.2.X Changelogs](/5.2.x_changelogs)
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