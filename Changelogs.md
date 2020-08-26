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



4.8.0
=====

 

Major Stuff
-----------

 

### Versions



-   Dropped 1.11 support (why aren't you on 1.12 yet?)



### AI Update



-   Many AI goals/targeters have been improved
-   Performance has been improved
-   A new API has been added for registering custom AI goals



### Villager Trades

 You can now configure villager trades! Please note that villagers
must have certain professions to be able to trade, and some items may
require the villager to be a certain level. 

    MerchantTest:
      Type: VILLAGER
      Display: '&6Merchant Test'
      Health: 20
      Faction: tester 
      Options:
        Profession: NITWIT
        Type: DESERT
        Level: 2
      Trades:
        1:
          Item1: 5 EMERALD
          Item2: 5 DIAMOND
          Result: DIAMOND_SWORD
          MaxUses: 5
        2:
          Item1: 64 EMERALD
          Result: SkeletonKingSword
          MaxUses: 1



### Chain Mechanic

  A really cool new mechanic! See entry in the mechanics section.


Commands
--------



-   Added -p flag to mob spawn command, allowing you to spawn mobs at
    aspecific player



Mobs
----



-   Added WANDERING_TRADER



### Options



-   Added **Options.PreventTransformation: true** to stop zombies from
    turning into pigmen or drowned



Mechanics
---------

 

### NEW: BarCreate



### NEW: BarSet



### NEW: BarRemove



### NEW: BlockWave

 Creates a wave of blocks. This effect is client-side (there is no
risk to your server). {{ :blockwave.gif?400 |}} 

### NEW: BloodyScreen



### NEW: Chain

 This allows you to make skills that bounce between targets, like a
"chain lightning" type skill.  BounceConditions are evaluated after
each "bounce" of the skill. With the example, if someone were on the
other side of a wall from the mob but you were standing in the doorway,
it could bounce from you to them since it bounced around the wall 
It will only bounce to the same entity per cast once. Also every time
the skill bounces, the entity it is bouncing from will be the "origin"
in the skill and the inherited target of onBounce will be the next
entity it is bouncing to, so fromOrigin is your friend for making
effects!  Example:

1.  chain{

<!-- -->

        bounces=5;
        bounceRadius=10;
        bounceDelay=1;
        hitSelf=false;
        hitPlayers=true;
        hitNonPlayers=true;
        hitTarget=true;
        onBounce=[
          - effect:particleline{p=flame;fromOrigin=true}
        ];
        bounceConditions=[
          - inlineofsight
          - hasaura{aura=damageResist} false
        ];
      } @target ~onTimer:20



### NEW: CloseInventory



### NEW: MountMe



### NEW: SendToast



### NEW: Stun

  An aura mechanic that will stun the target entity for its
duration. 

1.  stun{auraName=stunned;d=100;facing=true;onTick=[ -
    particles{p=crit;amount=10;hS=0.4} ]} @trigger ~onInteract



### Cast



-   Added skillName, showCastBar options to cast mechanic
-   The Cast mechanic will show a hologram castbar if showCastBar=true



### Damage



-   Added damageType option, can be set to whatever you want
-   You can use any custom damageTypes you define in DamageModifiers and
    in the onDamaged aura

 Here are some examples of this in action: 

1.  damage{amount=10;element=FIRE} @target ~onUse
2.  damage{amount=10;element=ICE} @target ~onUse



    DamageModTest:
      Type: COW
      DamageModifiers:
      - LIGHTNING 0.1
      - FIRE 2.0
      - AIR 1.0
      - ICE 0.5
      Skills:
      - message{m="Damaged by <skill.var.damage-type> for <skill.var.damage-amount>"} @PIR{r=50} ~onDamaged



### onDamaged



-   Added **damageMods** option, letting you create auras that apply
    damage modifiers.
-   Can also specify custom damageMods that you use in the damage
    mechanic

<!-- -->

    
      - onDamaged{
          auraName=damageResist;d=200;
          onTick=[
            - particles{p=flame;amount=10;hS=0.4}
          ];
          damageMods="FIRE 0.5"} @self ~onInteract



### Particles



-   Added campfire_cosy, campfire_signal particles
-   Allowed a bunch of placeholders in more mechanics



Conditions
----------



### NEW: EnchantExp



### NEW: EnchantLevel



### NEW: FoodSaturation



### NEW: FoodLevel



### NEW: LocalDifficulty

 

Targeters
---------

 

### New Sorters



-   Added new Target sorters 
    -   HIGHEST_HEALTH 
    -   LOWEST_HEALTH 
    -   HIGHEST_THREAT 
    -   LOWEST_THREAT



    @ThreatTablePlayers{sort=HIGHEST_THREAT;limit=5}    
    

### NEW: @RandomLocationsNearTargets

 

AI Goals/Targets
----------------



### NEW: NearestConditionalTarget

 A premium-only AI Targeter that will cause the mob to attack any
nearby entities that meet the supplied conditions.  Example:

    AITargetSelectors:
    - clear
    - nearestConditionalTarget{conditions=[
          - entitytype PLAYER
          - hasaura{aura=marked_for_death}
        ]}



### NEW: FleeConditional

 A premium-only AI Goal that will cause the mob to flee from any
nearby entities that meet the supplied conditions.  Example:

    AIGoalSelectors:
    - clear
    - fleeConditional{distance=5; speed=2; conditions=[
          - inlineofsight
          - entitytype COW
        ]}



Placeholders
------------



-   Added missing trigger.threat placeholder



Compatibility
-------------

 

### LibsDisguises



-   Fixed some disguise bugs



Bug Fixes / Other
-----------------



-   Added better error catching for placeholders
-   Most mob config keys can now be lowercase if desired
-   Removed some outdated methods for determining mob type
-   Fixed ParticleAtom effect on 1.13+
-   Fixed bugs with global variables
-   Fixed some issues with goToOwner AI goal
-   Fixed bug with BlockUnmask effect
-   Fix for BLOCK projectile bullets on pre1.13 versions
-   Fixed inline conditions not working inside of metaskills
-   Fixed variableMath mechanic adding instead of setting values
-   Fixed NPE with target.name placeholder
-   Fixed some compatibility issues with WorldGuard on 1.8
-   Fixed plugin not loading on 1.8.8 PaperSpigot
-   Fixed a mob loading error on 1.8
-   Fixed hasParticles=false in potion mechanic
-   Fixed NPE when creating spawners that use mpets
-   Fixed vault currency reward messages to be rounded to 2 decimal
    places
-   Fixed some issues with bstats
-   Fixed a bunch of broken AI targeters on 1.14
-   Fixed bug with goToOwner AI goal
-   Fixed NPE in rally mechanic
-   Fixed NPE in @MobsInRadius targeter
-   Fixed numerous bugs with auras
-   Fixed projectiles hitting and stopping on non-creatures
-   Fixed projectile mob bullets sometimes getting stuck and not
    despawning
-   Fixed some inconsistencies with ThreatTables
-   Fixed mob sometimes not being marked in combat when targeting
    players
-   Fixed ThreatTable mobs continuing to target players that died
-   Fixed onDropCombat skills sometimes firing twice
-   Fixed sounds playing with infinite range on 1.14
-   Fixed some bugs with the Wearing condition
-   Fixed some bugs with item NBT
-   Fixed some bugs with shootFireball
-   Fixed creeper damage being modified when it shouldn't
-   Fixed some bugs with targeters
-   Fixed some issues with the prison mechanic



4.7.1 [Latest]
================



-   Fixed several bugs with placeholders
-   Fixed number ranges not working in drops
-   Backported several other random bug fixes



4.7.0
=====

 

Major Features
--------------

 

### 1.14 Support



-   Full support for 1.14.4
-   Dropped support for 1.7, 1.9 and 1.10



#### New Mobs



-   Cat
-   Fox
-   Panda
-   Pillager
-   Ravager



#### New Particles



-   flash
-   landinglava
-   sneeze
-   composter
-   fallinglava
-   fallingwater



### Better MetaSkills

 MetaSkills can now in many places be put in-line instead of having to
reference another skill. This means you will no longer have to make
multiple small skills in order to use certain complex meta-skills, such
as projectiles.

    

This is done by creating a new list of mechanics surrounded by square
brackets []s instead of putting a skill name. You can do this to nest
skills pretty much infinitely. Each new list of skills should be
properly indented to make sure YAML reads them correctly. 

    
    Skills:
    - projectile{
          interval=1; velocity=30; bulletType=BLOCK; material=MAGMA_BLOCK; tyo=0.5; g=1; bulletSpin=-40; hnp=true; stopatentity=false; duration=100;
          onHit=[
              - damage{amount=50}
              - ignite{ticks=20}
          ];
          onTick=[
              - particles{p=flame;a=20;hs=0.5;vs=0.5}
          ];
          onEnd=[
              - particles{p=largeexplode;a=50;speed=1;hs=0.05;vs=0.05}
              - effect:sound{s=entity.dragon_fireball.explode;p=0.6;v=2}
              - damage{amount=30} @ENO{r=5}
          ];
      } @targetlocation



### Math/Placeholders

 **This feature is Premium-only**.  You can now use math and
numeric placeholders in lots of places! The plan is to expand this to be
usable anywhere, but it's a big undertaking.  In order to use math
where able, you can simply put placeholders and equations between ''
where you'd normally put a number value.  For example:

    Skills:
    - damage{amount=1}
    - damage{amount='5 + 5'}
    - damage{amount='<caster.level> * 10'}

 and so on  The following mechanics can use math so far:

-   **damage**
-   **damagePercent**
-   **heal**
-   **healPercent**
-   **setLevel**

 Math is also usable in drop amounts:

    Drops:
    - gold_nugget '1 + (0.2 * <caster.level>)'



### Projectile Bullets

  Projectile mechanics can now specify a bullet type that will
represent the projectile. No longer are projectiles just limited to
particles!  These work with the projectile, missile, and orbital
mechanics.  Bullet types available are:

-   **ARROW** - *projectile{bulletType=ARROW;...}*
-   **BLOCK** - *projectile{bulletType=BLOCK;material=STONE;...}*
-   **ITEM** - *projectile{bulletType=ITEM;material=STONE;...}*
-   **MOB** - *projectile{bulletType=MOB;mob=SkeletonKing;...}*

 Yes, that's right, you can even shoot projectiles made up of other
Mythic mobs! Mobs shot with the projectile skill cannot be interacted
with, but will still use all their skills...  You can also use the
new **bulletSpin=#** option to give your bullets some spin. 

Mobs
----

 Added support for all 1.14 mob types. 

Mechanics
---------

 

### NEW: onShoot

 A special Aura mechanic that adds a temporary onShoot skill to the
target.

    Skills:
    - onShoot{auraName=fireball_bow;onShoot=[ shootfireball ];duration=200;charges=5} @self

 In this example, the caster's next 5 bow shots will shoot fireballs
instead of arrows. 

### NEW: Speak

 Speak is similar to the message skill, but is used for making mobs
"talk". Mobs will talk in the chat using a configured syntax, and if you
have a hologram plugin installed, they will also have speech bubbles!


     - speak{m="OH BOY I HAVE SPEECH BUBBLES NOW"} @trigger ~onInteract
     - speak{m="OW THAT HURTS I CANT BELIEVE YOU WOULD HIT AN INNOCENT MAN"} @trigger ~onDamaged 

 {{:od8f7goejm.gif?400 |}} 

### NEW: VariableMath

 

Conditions
----------

 

### NEW: DamageAmount

 

### NEW: DamageCause

 

### NEW: Health

 

### NEW: Moving

 

Items
-----



-   Added the **Model** option for setting an item's CustomModelData NBT
    tag. 
-   Placeholders and variables are now usable in item lore



Drops
-----

 

### Math



-   ***Premium Only*** You can now use math equations and placeholders
    in drop amounts, surrounded by single-quotes.
-   Drop messages now use regular placeholders



### NEW: cmd



-   Added a new drop type to run a command for the killer



Placeholders
------------



-   Name-related placeholders will now show the entity's type instead of
    Unknown if the mob has no name
-   Added &lt;trigger.luck&gt; placeholder
-   Added &lt;caster.enchantlevel.ENCHANT_NAME&gt; placeholder
-   Added &lt;caster.heldenchantlevel.ENCHANT_NAME&gt; placeholder
-   Added &lt;&nm&gt; placeholder for number signs #



Spawns
------



-   Regular mobs will now obey the MaxMobsPerChunk option



Compatibility
-------------

 

### Holographic Displays

 All hologram-related things now support using Holographic Displays,
including health bars, nameplates, and speech bubbles. 

### LibsDisguises



-   Added a bunch of missing disguises



Bug Fixes / Other
-----------------



-   Fixed some bugs with serialization
-   Fixed missiles to hit the target's body instead of their feet
-   Fixed wearing condition
-   Fixed some egg-related crashes on 1.14
-   Fixed placeholders in drop messages
-   Fixed singlequotes breaking message mechanics
-   Fixed &lt;.php&gt; placeholders
-   Fixed the shootpotion mechanic
-   Fixed a bunch of errors related to world unloading
-   Fixed despawn event throwing an async error
-   Fixed despawning errors on shutdown
-   Fixed xp messages showing up even when disabled
-   Fixed droptable inline item display names not parsing special
    characters
-   Fixed inline OnBlock and WorldTime conditions
-   Fixed an error with recursive drops
-   Fixed several variable-related bugs
-   Fixed custom API drops not rolling amounts correctly
-   Fixed various errors with Random Spawns
-   Fixed particle effects appearing in the wrong world
-   Fixed delayed skills throwing errors when the world was unloaded
-   Fixed toggleLever not obeying the set duration
-   Fixed another error with shootpotion
-   Fixed MythicMobs breaking the Guilds plugin
-   Fixed onSurface option in summon mechanics



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