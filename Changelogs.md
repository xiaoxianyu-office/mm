4.11.0  (Development Builds)
=====

Mechanics
----

### onAttack Aura
- Allow placeholders in damageAdd, damageMultiplier

### NEW: BlockPhysics
### NEW: FawePaste

Effects
----

### Particle Effects
- Added dir=x,y,z option to particle effects to specify directional vector

Targeters
---------
### General
- Added yaw and pitch to @Location targeter
- Upgraded raytrace mechanic to shoot thru barrier blocks

### NEW: @CasterSpawnLocation
### NEW: @ObstructingBlock
### NEW: @FloorOfTargets meta-targeter
### NEW: @LocationsOfTargets meta-targeter

Conditions
----------
### NEW: HasPassenger

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