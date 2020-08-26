4.10.0  (Development Builds)
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

### NEW: RayTrace
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

4.9.1
=====



General
-------
-   Updated to use latest LibsDisguises
-   Updated to use latest version of MMOItems
-   Data files will now regenerate when corruption is detected and leave
    a backup of the old file

Mechanics
---------



### Command



-   Added asTarget option to Command mechanic
-   Added requireTarget option to Command mechanic



### Summon



-   Added level attribute to summon mechanic



Conditions
----------



### NEW: mobsInRadius



    mobsInRadius{types=X,Y;amount=minToMax;radius=#}    



Disguises
---------



-   Added Disguise.Name option
-   Better PlayerDisguise parsing for LibsDisguises
-   Disguise.ShowName for mobdisguise should be assumed false



Bug Fixes/Other
---------------



-   Added more error catching for badly configured items
-   Fixed plugin not even loading on 1.12
-   Fixed errors in ProtocolLib support
-   Fixed MountMe, MountTarget mechanics running async
-   Fixed PotionMechanic overwrite=true not working on 1.15
-   Fixed offset not working in speak mechanic
-   Fixed serialization error with spawn location and goToSpawn AI
    goal
-   Fixed NPE preventing removed or corrupted mobs from being cleaned up
    
-   Fixed projectiles hitting targets multiple times in the same hit
-   Fixed Custom drops not registering on startup
-   Fixed GoToOwner goal error when player owner changes worlds
-   Fixed NPE in FleeIf AI goal
-   Fixed NPE in SudoSkill mechanic
-   Fixed wandering_trader and baby_wandering_trader disguises
-   Fix names on custom player disguises not being set properly
-   Fixed NPE when chain mechanic has no target
-   Fixed bugs with lunge mechanic
-   Fixed PreventSlimeSplit option
-   Fixed eggs spawning pigs out of dispensers
-   Fixed TriggerLocation targeter
-   Fixed villager trade results not working with multiple amounts
-   Fixed RemoveAura mechanic not working with targets
-   Fixed dusk condition logic being backwards
-   Fixed remount mechanic running async
-   Fixed custom AI errors on 1.13
-   Fixed corrupt spawner files so that they'll still load if they have
    lost their world data so they can still be updated/moved
-   Fixed spawners losing their data if they fail to load the mob type
-   Fixed and optimized tracking of number of entities per chunk
-   Fixed vanilla mob spawns not obeying MaxMobsPerChunk setting



4.9.0
=====

 

Major Stuff
-----------

 

### Versions



-   Dropped 1.8 Support (Seriously, what are you doing?)
-   ADDED 1.15.x Support



### NEW: Packs

 You can now create "packs" of things. To create a pack, you make your
pack folder in the "Packs" folder and then put your pack stuff in your
pack folder in the Packs folder.  For example, to create
MyCoolMobPack, you could organize your stuff like this: -
plugins/MythicMobs/Packs/MyCoolMobPack/Items -
plugins/MythicMobs/Packs/MyCoolMobPack/Mobs -
plugins/MythicMobs/Packs/MyCoolMobPack/Skills  This should make it
easier for people to organize and distribute stuff. Packs can contain
DropTables, Items, Mobs, Skills, and RandomSpawns, and also Artifacts'
Enchantments 

### Commands



-   Added yaw and pitch options to spawn command



Mobs
----



-   Added Bees
-   Added TRADER_LLAMA
-   Fixed Vindicator Mob type
-   Added 1.14+ Cat support
-   Mob Levels can now have decimal places for smoother scaling.



### Options



-   Options.Anger (Bees)
-   Options.HasNectar (Bees)
-   Options.HasStung (Bees)
-   Options.ApplyInvisibility (true/false) (No more 10000 duration
    invisibility potions ~onSpawn)
-   Options.HasBasePlate (Armor Stands)
-   Options.MainGene, Options.HiddenGene (Panda enum names)
-   Options.FoxType (Foxes)
-   Options.OcelotType (Cats)
-   Options.LockPitch (Requires protocollib, keeps mobs heads from
    looking up/down)
-   Options.CanTick, Options.CanMove (ArmorStand option on
    Paperspigot)
-   Options.PreventJockeyMounts (for zombie types)



Mechanics
---------



-   Improved nearestOtherFaction AI targeter
-   Added doNothing{conditions=[]} AI goal (premium-only)
-   Added usePlayerName option to the doppleganger mechanic
-   Added 'disguisetarget' mechanic
-   summon mechanic now has "inheritFaction=true/false" option
-   sendtoast{}

1.  added option "[icon]nbt=string" (default = nothing)
2.  sendtoast{icon="diamond_sword",iconnbt="{CustomModelData:3}",frame="goal"}
3.  sendtoast{icon="shears",nbt="{Damage:10b,Unbreakable=true}",frame="challenge"}



-   Added placeholder support to "shoot" and "volley" mechanics.
-   Added placeholder support in the 'setname' mechanic.
-   Allow placeholders in in-line delay, repeat, and repeatInterval



-   Added &lt;caster.l.yaw&gt; and &lt;caster.l.pitch&gt;
-   Added option "soundcategory" to effect:sound{}
-   Added sendMessage=false option to currency drops



### NEW: Animate Armorstand



    *New mechanic: animatearmorstand{} / alias: animas{}
    Options:
    - duration=ticks (default = 1)
    - head = x,y,z
    - body = x,y,z
    - leftarm = x,y,z
    - rightarm = x,y,z
    - leftleg = x,y,z
    - rightleg = x,y,z
    - smart = boolean (default = true)
    - ignoreempty = boolean (default = true)
    - usedegrees = boolean (default = true)
    ----------------------------------------
    * "smart" will help you to make your animations smoother if true
    * "ignoreempty" will ignore unspecified body parts and not animate them
    * "usedegrees" interprets the input' values as degrees (0-360) and as radians (0-6.28) if set to false



    Examples:
    - animatearmorstand{d=60;head=45,0,0}
    - animatearmorstand{d=10;leftarm=90,0,0;rightarm=270,0,0;ignoreempty=false}
    - etc, any combination you like



### NEW: setrotation



-   Added setrotation{} mechanic:

1.  setrotation{relative=true;yaw=90}
2.  setrotation{yaw=0;pitch=0}
3.  setrotation{relative=true;pitch=-45}



### NEW: disengage



-   Added 'disengage' mechanic for properly lunging backwards.



### NEW: setAI



-   setAI{ai=true/false}



### NEW: setMobColor



-   SetMobColor{color=X}



### NEW: giveItem

 

### NEW: teleportto



    *Added 'teleportto{}' mechanic, with support for relative teleportation.
    - teleportto{m=relative;c=0,1,0} (teleports the target 1 block above its' current location)
    - 
    * Added support for directional teleportation:
    - teleportto{m=directional;c=1,0,0} (teleports the target 1 block towards its current facing (yaw))
    - teleportto{m=directional;c=1,0,1} (teleports the target 1 block forward and 1 to the right)
    - teleportto{m=directional;c=-1,3,0} (1 block backward + 3 blocks up)
    - teleportto{m=directional;c=0.1,0,0;yaw=1} (adds 1 to targets' yaw and teleports 0.1 blocks forward)
    - Added option "origin=caster/target" for basing the origin of directional/relative teleportation
    - Allow placeholders in TargetTo and TargetIn mechanics



### IMPROVED: Threat



-   Added more functionality to the threat{} mechanic.
-   The threat mechanic now supports the "mode=" field which includes
    the options:

1.  mode=add (default value)
2.  mode=remove
3.  mode=multiply
4.  mode=divide
5.  mode=set (allows setting threat to specific value)
6.  mode=reset (removes the target from the threat table)
7.  mode=forcetop (forces the target to become the top threat holder)

<!-- -->

    set/reset/forcetop do not require the "amount=" field



### Particle Effects



-   Added dripping_honey
-   Added falling_honey
-   Added falling_nectar
-   Added landing_honey
-   Added xSpread and zSpread option for all particle effects



Targeters
---------

 

### Origin Targeter



-   Added yoffset option



### Target Filters



-   Added ignore=vanilla/targetvanilla=false target filter
-   Added 



Conditions
----------



-   Added 'hasGravity' condition
-   Added 'children' condition, which tests how many children the caster
    has



### NEW: SameFaction

 

Placeholders
------------



-   Added caster.tt.size placeholder
-   Added placeholder support to "shoot" and "volley" mechanics.
-   Added placeholder support in the 'setname' mechanic.
-   Allow placeholders in in-line delay, repeat, and repeatInterval
-   

Items
-----



-   Added Options.AppendType to items, to track MM Item Type in NBT



Spawners
--------



-   Added &lt;spawner.pir&gt; (players in radius) placeholder for
    spawners to set mob amount based on players in radius.
-   Added scalingRange attribute for spawners
-   Allow placeholders+math in spawners maxmobs attribute
-   Allow multiple mob types per spawner, in format:

<!-- -->

    /mm s set [name] mobtype 25%Mob1,25%Mob2,50%mMob2



Compatibility
-------------



-   Better FactionsAPI support
-   Added native support for latest MMOItems/MMOCore



### LibsDisguises

 Added missing disguises:

-   baby_horse
-   baby_mooshroom
-   baby_chicken
-   baby_pig
-   baby_sheep

<!-- -->

    

PREMIUM ONLY
------------



-   Mob Health and Damage now support math and placeholders.
-   Added new ScalingEquations in config.yml to auto scale mob
    health/damage using math/formulas. Replaces Levelmodifiers if
    used.}
-   Item attributes can now use placeholders/math for item generation.
-   doNothing{conditions=[]} AI goal



Bug Fixes/Other
---------------



-   Improved MythicMobSpawnEvent
-   Fixed onAttack skills recursively triggering themselves
-   Fixed projectiles sometimes hitting their own bullets and stopping
-   Fixed projectiles not terminating in unloaded worlds
-   Fixed mpets working with mob spawners
-   Fixed mpets working with summon skill
-   Fixed error with HolographicDisplays support
-   Fixed recursive onDamaged skills with mob damaging itself
-   Fixed remove command not unregistering non-Despawning mobs
-   Fixed Lunge and Disengage mechanics not targeting locations
-   fixed some item related bugs
-   fixed some Item NBT bugs
-   fixed RandomThreatTarget targeter never targeting the last person on
    threat
-   fixed lunge being backwards and changed velocity to absolute value
-   Fixed several placeholder/math bugs.
-   improved 1.15.1/1.15.2 compatibility
-   Fixed several spawner related bugs.
-   Fixed MythicMobDespawnEvent being async
-   fixed ranges/percents in attributes
-   Fixed Options.PreventTransformation
-   Fixing mixup of x/z axis in mode=relative on teleportto{}
-   Fixed yaw in mode=relative / teleportto{}
-   Fixed NPE in TeleportIn mechanic
-   More placeholder support
-   Made parrots randomize color if not specified
-   Fixed Options.PassthroughDamage not working with projectiles.
-   Fixed a bullettype material error
-   Fixed Parrots
-   Scaling equations may now be set to NONE
-   Fixed onCombat trigger
-   Improved Paper compatibility
-   Fixed double/float ranges using #-# format not parsing
-   Fixed spawners set and listnear commands
-   Fixed armor stands having no gravity by default
-   Fixed an NPE with CreatureSpawnEvent
-   Fixing effect:sound being played globally maybe
-   Fixed NPE in OtherFaction AI goal
-   Deprecated backup system for tracking mob type in scoreboards
-   Fixed compatibility error with HolographicDisplays
-   a bunch of other stuff I probably forgot







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