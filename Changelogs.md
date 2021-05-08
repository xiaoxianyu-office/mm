4.12.0 (Dev Builds)
======

General
-------

Mobs
----


Mechanics
---------

### Projectiles
- Greatly improved block collision detection
- Improved collision detection with huge mobs (giants, ghasts, etc)
- Improved collision detection with ModelEngine mobs


Effects
-------

### Audiences
- Added *caster* audience
- Added *@targeter* audience, allowing you to use any entity-targeter as an audience

### Particle Effects - Mob particles???
- Added special type particle=mob on all particle effects
- You can then specify a MythicMob using mob=[type]
- This is a hacky way for you to use mobs as "particles" in effects using no-tick ArmorStands wearing models or using font characters. You can use things other than ArmorStands if you want, but we don't recommend it for performance.

Targeters
---------


Conditions
----------
### NEW: isCaster
### NEW: 
### NEW: 
### NEW: isSprinting
- only works on players


```
- size >5
```

Items
-----

Placeholders
------------
- Added <caster.l.x.double>
- Added <caster.l.y.double>
- Added <caster.l.z.double>
- Added <skill.targets>

Compatibility
-------------
- Updated to latest LibsDisguises
- Removed CMI support completely
- Removed unused EffectLib compatibility

Bug Fixes/Other
---------------
- Fixed @ring targeter being slightly off-center
- Fixed audiences not working with certain particle effects
- Fixed invisible armorstands flickering for a tick when spawning
- Fixed an NPE in metaskills
- Fixed certain things such as bullets not showing up until after a reload
- Fixed NPE when spawning certain mobs on non-paper servers


4.11.0
======

General
-------
- Added support for 1.16.4

Mobs
----
- Added PIGLIN_BRUTE, BABY_PIGLIN_BRUTE
- Changed Options.PreventItemPickup to default to true

Mechanics
---------

### onAttack Aura
- Allow placeholders in damageAdd, damageMultiplier

### Orbitals
- Added projectile bullets to Orbital

### Shoot & Volley
- Added Trident projectile type
- Added splash_potion and lingering_potion projectile types
- Added most of the options from the Projectile mechanic to Shoot & Volley

### ShootFireball
- Added type=[SMALL/LARGE/DRAGON] attribute

### NEW: BlockPhysics
- Triggers a block physics update at the target location
### NEW: PotionClear
- Clears all potion effects from the target entity
### NEW: Extinguish
Removes any fire ticks from the target entity
### NEW: FawePaste
### NEW: Oxygen
Gives the target player an amount of oxygen
```
- oxygen{amount=10}
```
### NEW: setNoDamageTicks
Sets the immunity ticks on the target. Should be delayed if used immediately during an attack since the ticks are applied after an event completes.
```
- setNoDamageTicks{ticks=0;delay=1} @trigger ~onAttack
```
### NEW: Swap
Swaps positions of the caster and the target entity.
### NEW: WolfSit
Sets the sitting state of the target wolf
```
- wolfSit{state=true}
```

Effects
-------

### Particle Effects
- Added dir=x,y,z option to particle effects to specify directional vector
- Added audience=[world/target] options to all particle effects

### NEW: TotemUndying effect
- Plays the effect of a totem resurrecting a player
- Can specify a model to use from texture packs to overlay on the player's screen
- No you can't disable the sound :(
```
- totemUndying{model=2}
```

Targeters
---------
### General
- Added yaw and pitch to @Location targeter
- Upgraded raytrace mechanic to shoot thru barrier blocks

### NEW: @BlocksInRadius{r=#} location targeter
### NEW: @CasterSpawnLocation
### NEW: @ObstructingBlock
### NEW: @FloorOfTargets meta-targeter
### NEW: @LocationsOfTargets meta-targeter

Conditions
----------
### Moving
- Updated moving condition to work with players
### NEW: HasPassenger
### NEW: Burning // isBurning
### NEW: SlimeSize
```
- size >5
```

Items
-----
### NBT Tag Improvements
- Added ability to specify data type for NBT tags
```
AnItem:
  Id: EMERALD
  NBT:
    AnInteger: int/32
    ADouble: double/50.0`
    AByte: byte/1
```

API
---
- Added MythicMobItemGenerateEvent, called whenever an item is being generated

Bug Fixes/Other
---------------
- Ignore non-natural spawns for RandomSpawns
- Fixed NPE in mob listener
- Fixed ignoreSpectator and ignoreCreative target filters
- Fixed new colors on items breaking spigot closes #38
- Fixed item loading errors on 1.16.2 non-paper spigot
- Fixed JsonMessage mechanic (requires testing) closes #77
- Fixed blockmask effects restoring wrong blocks when ending, closes #75
- Fixed message mechanics on non-paper spigot closes #80
- Fixed haspotioneffect condition closes #18
- Fixed in-line target conditions requiring a reload before working
- Fixed mobs spawning at level 0 instead of 1 when spawned via command
- Fixed NPE caused by mob types that have been removed
- Fixed NPE with BlockWave effect
- Fixed auras executing async-unsafe mechanics async
- Fixed recursive spawning overflow
- Fixed mobs spawned by eggs sometimes spawning in walls
- Fixed PreventBlockInfection option for silverfish
- Fixed targeters not targeting creative players when they should
- Fixed crash caused by remove mechanic running async on 1.16
- Fixed NPE with location targeter
- Fixed SpecificFaction AI Targeter on 1.16
- Fixed error in spawner find command on non-paper builds
- Fixed concurrency error with skills closes #186
- Fixed a bunch of AI bugs on 1.16+
- Fixed bugs with setLevel mechanic running async
- Fixed temporary player error with protocollib support
- Fixed bugs with fly mechanic
- Fixed orbital mechanic not executing onEnd skills
- Fixed more issues with specificFaction AI goal working on players
- Fixed skills in projectiles and auras not being properly marked as async
- Fixed concurrency issues with @EIR targeter closes #210
- Fixed particle effect direction not setting z value correctly
- Fixed mob spawning bugs on 1.12
- Fixed OtherFactions AI on 1.12
- Fixed error when negative heal values try to set health <0
- Fixed NPE in projectile mechanic
- Fixed LevelModifiers to be prioritized over using global scaling equations
- Fixed Worldtime Condition
- Fixed issues with world audience on sound effect
- Fixed some concurrency issues with mobs
- Fixed bullet mobs on projectiles not setting caster as parent
- Fixed placeholders not working on spin effect
- Fixed DisableVanillaSpawns blocking mobs from RandomSpawning
- Fixed doppeganger mechanic on mobs without display names
- Fixed some issues with onHit skills w/ the shoot and volley mechanics
- Fixed inheritFaction=false w/ summon mechanic
- Fixed NPE in Projectile mechanic
- Fixed some issues with onHit skills w/ the shoot and volley mechanics
- Fixed vanilla override mobs dying instantly glitching out
- Fixed NPE with invalid mmoitem drops that could cause mobs to break when dying
- Fixed NPE in ParticleOrbital
- Fixed localized lightning effect on 1.16
- Fixed bossbar mechanic firing after mob is dead
- Fixed several bugs caused by mob spawning being cancelled
- Fixed bossbar blinking + some other issues
- Fixed toast mechanics not revoking fake criteria
- Fixes for lightlevel condition
- Fixed blockwave fake blocks using wrong data values on 1.12
- Fixed damage that ignores armor not triggering totems
- Fixed @target targeter throwing error on item timer skills
- Fixed drop table error with items w/ amount=0
- Fixed @target w/ players going thru solid transparent blocks
- Fixed setOwner mechanic not working with Cats and Parrots
- Fixed several item-related bugs
- Fixed NPE with Location mechanics targeting entities
- Fixed bug with mobs becoming invincible when dying during the same tick they spawn
- Fixed several bugs with aura mechanics
- Fixed wearing condition breaking with durability and vanilla items
- Fixed setOwner mechanic issues
- Fixed animateArmorStand mechanic
- Fixed ClassCastException thrown by damage mechanic
- Fixed unidentified items with mmoitems drops
- Fixed tridents not working with shoot mechanic
- Fixed raytracing to non-damageable entities throwing an error
- Attempted to fix item serialization in 30 different ways
- Removed unused EffectLib compatibilities
- Removed ClickEvent

4.10.0
=====

General
-------
- Added support for 1.16, including all the 1.16 mobs and particles
- Added support for 1.16.2, including Piglin Brutes
- Added in-line target conditions (premium-only)
- Improved world data saving
- Removed lots of deprecated methods, updated libraries and cleaned up

New Mobs
----
- PIGLIN
- HOGLIN
- ZOGLIN
- BABY_HOGLIN
- BABY_ZOGLIN
- STRIDER
- PIGLIN_BRUTE

### Piglins
- Added AbleToHunt, ImmuneToZombification options to Piglin

### Hoglins
- Added PreventZombification option to Hoglins

Mechanics
---------
### General / Small Stuff
- Added 1.16 particles: crimson_spore, soul_fire_flame, warped_spore, dripping_obsidian_tear, falling_obsidian_tear, landing_obsidian_tear, and soul
- Allow math in variableSet mechanic
- Added more placeholder support to Aura mechanic
- Added placeholder support to prison mechanic
- Added placeholder support to healPercent mechanic
- Added placeholder support to Lunge mechanic
- Slightly increased attractiveness and performance of AnimateArmorStandMechanic

### Message / Speak
- Now allow hex colors in the format **`<#FFFFFF>`**
- Now supports gradients in the format **`<gradient:#color1:#color2>text</gradient>`**
- Now supports **`<rainbow>text</rainbow>`**
- Now supports hover text in the format **`<hover:show_text:'hover text??'>hover over me!</hover>`**
- Now supports clickable text in the format **`<click:run_command:/say hello>click me!</click>`**

### Missile
- Missiles can now target locations
- Added targetYoffset to missile mechanic

### NEW: RayTrace (premium-only)
### NEW: RayTraceAt (premium-only)
### NEW: Recoil Effect
### NEW: PlayBlockBreakSound (paper-only)
### NEW: PlayBlockFallSound (paper-only)
### NEW: PlayBlockHitSound (paper-only)
### NEW: PlayBlockPlaceSound (paper-only)
### NEW: PlayBlockStepSound (paper-only)

Conditions
----------
### General / Small Stuff
- Added exact option to moving condition, defaults to false
### NEW: EnderDragonPhase condition
### NEW: LivingInRadius condition
### NEW: YDiff condition

Targeters
---------
### General
- Allow placeholders in @RLNT targeter amount
- @Location targeter can now use placeholders

### NEW: @Siblings
### NEW: @RTTL / Random Threat Target Location

Placeholders
------------
- Added various parent. placeholders

Items
-----
For item names and lore:
- Now allow hex colors in the format **`<#FFFFFF>`**
- Now supports gradients in the format **`<gradient:#color1:#color2>text</gradient>`**
- Now supports **`<rainbow>text</rainbow>`**

Bug Fixes/Other
---------------
- Fixed loading old imported bukkit items
- Fixed world and global variables not loading properly after restarts
- Fixed numerous issues with serialization and saving between restarts
- Fixed various bugs with variables
- Fixed some broken options that apply after mob death e.g. SlimeSplit
- Fixed issues with biome condition
- Fixed RandomSpawners not working on entities in newly generated chunks
- Fixed SendActionMessage mechanic on non-paper versions
- Fixed some bugs with target filters
- Fixed error in drops when mobs killed by non-entity w/ Luck Mods
- Fixed repeated mechanics looping forever if they throw an error
- Fixed NPE when saving PlayerData with certain variables
- Fixed DawnCondition not working
- Fixed NPE caused by mob types that have been removed
- Fixed entitytype condition not using conditionVar
- Fixed mechanic-level cooldowns not respecting decimals
- Fixed PAPI support




Older Changelogs
================

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