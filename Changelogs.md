5.4.0 (Dev Builds)
=====

Highlights
----------
### Version support
Added support for 1.20.2

### Projectile Bullets
- Added DISPLAY and TEXT bullet types

- Item Display Bullet Type: Add "tx", "ty" and "tz" (t from translation) to offset the visual position of the bullet, also "translation"("pos", "offset") to set all the values at the same time in the x,y,z format

- Added `bulletBrightness`, and `bulletBrightnessBlock` + `bulletBrightnessSky` for some reason to Display bullets
- Added `bulletBillboard` to Display bullets

### Stat System

### Holograms

- Made it so mob names can be multi-line using nameplates feature on 1.19.4+ using `\n` for newlines

### Spawners
- Major spawners rewrite - see spawners section

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

### AI
- Added `radius` option to `LookAtPlayers` goal

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

### NEW: ClearExperienceLevels

### NEW: pushBlock
- Pushes the targeted block in the given direction. Follows the same rules as pistons.
- Direction can be either cardinal direction or a location targeter. If given a targeter, the block will be pushed once towards that location
- Mechanic also supports `onPush` and `onFail` skills which will fire at the block's location

Mechanic follows piston rules and will push other connected slime blocks as well, but only if they're adjacent or in front of the block - it cannot push connected blocks _behind_ the pushed block.

### NEW: `setProjectileDirection`
- Changes calling projectile's direction to the given target

### NEW: `setProjectileBulletModel
- Added `setProjectileBulletModel{model=X}` mechanic, can be called by a projectile to change the bullet's item's model ID (only works with DISPLAY bullets)

### ArrowVolley
- Add "pickup"/"canPickup" attribute, defaults to true

### Damage Mechanics
- Added `powerAffectsDamage`, `ignoreShield`, `ignoreEffects`, `ignoreResistance`, `damagesHelmet`, and `noAnger` boolean options to damaging mechanics

### Particle Effects
- Added new particles: DRIPPING_CHERRY_LEAVES, FALLING_CHERRY_LEAVES, LANDING_CHERRY_LEAVES
- Added `startSideOffset` placeholder support to particle effect mechanic

### Projectile Mechanics (Projectile, Missile, etc)
- Added `tickInterpolation` option (defaults to 0)
- Changed mob bullet's Y offset option to bulletYOffset

Setting tickInterpolation will interpolate that many points between each tick in a projectile and execute the onTick and onHit skills on those points as well, doing multiple 'ticks' in a single tick.

This can be used to fill in the gaps with super-fast projectiles and also prevent entities from being skipped over by insanely fast projectiles.

- Added `interactable=true`, `onInteractSkill` to projectiles (requires 1.19.4+), used to allow the player to hit the projectile similar to a ghast fireball.

### Missile
- Added `hugSurface` and `bounce` options to missile mechanic (and all other related options similar to the Projectile mechanic)

### Lunge
- Added `oldMath/old/o` attribute to determine if it should use the old wonky math (default: false)

### Orbital
- Added `hugSurface` to orbitals

### PotionClear
- Added `type`/`types` attribute to `potionClear` mechanic

### Volley
- Add "pickup"/"canPickup" attribute, defaults to true

Conditions
----------

### NEW: directionalVelocity

Added `directionalVelocity` condition, which checks if the target has a velocity matching the given parameters.

Options:

| Option | Description | Default |
|--------|-------------|---------|
| x | The X velocity (a range) | null (not checked) |
| absx | Use the absolute value of the X velocity | false |
| y | The Y velocity (a range) | null (not checked) |
| absy | Use the absolute value of the Y velocity | false |
| z | The Z velocity (a range) | null (not checked) |
| absz | Use the absolute value of the Z velocity | true if relative=true, otherwise false |
| relative | If true, X is calculated as forward/backward and Z is side-to-side | false |

If the X, Y, or Z velocity is not specified, that component of the velocity is not checked. The 'absx', 'absy', and 'absz' options determine whether the absolute value of the corresponding velocity is used in the check. If 'relative' is true, the velocities are considered relative to the entity's orientation.

Audiences
---------
- Added TRACKED audience, which are the players that are rendering the caster on their client

Placeholders
------------

### General
- Added `<caster.stat.STAT_NAME>` placeholders
- Added `<target.block.data>` - returns the block data of a block
- Added `<target.item.type>` placeholder

### NEW: Custom Placeholders

Added custom placeholders file to make it easier to configure static/reusable and even conditional values.

Each pack can now have a `placeholders.yml` in the base pack directory that contains any number of placeholders.

These can be static or you can define conditional placeholders - the first one that evaluates true will be chosen, or the Default if they're all false.

An example placeholders.yml might look like this:
```
TestPlaceholder: 'some value'
TestConditionalPlaceholder:
  Day:
    Conditions:
    - day
    Value: day
  Night:
    Conditions:
    - night
    Value: night
  Default: idk

Added ability to define random placeholders that will just choose a random line from a list in the `placeholders.yml` file
```
TestRandomPlaceholder:
- red
- green
- blue
  ```

Stats
-----


Spawners
--------
- Rewrote spawner saving/loading
- Rewrote spawner positioning algorithm
- Added SpawnConditions to spawners that target the position it's trying to spawn a mob
- Regular conditions continue to function as "Activation Conditions" e.g. does the spawner even try
- Added tab completion to a lot of the spawner commands
- Fixed various spawner related bugs
- Made some API changes for 5.5, which will add a GUI editor for spawners

Bugs / Other
------------
- Fixed NoSuchMethodError in CrouchingCondition
- Fixed spawner config field for spawn conditions to actually be SpawnConditions
- Fixed loading error on 1.16
- Fixed remove attribute on SetLeashHolder mechanic
- Fixed @targetlocation targeting block location instead of actual location when hitting maxDistance for players
- Fixed projectiles with no hitboxes being broken
- Fixed default values for PlayersInRingTargeter
- Fixed ClassNotFoundException on mohist
- Fixed `preventImmunity` option to DamageMechanics
- Fixed/removed vehicle alias from the mount targeter
- Fixed spawner addcondition command not saving conditions after a restart
- Fixed issues with removing spawner conditions
- Fixed `<target.block.type>` placeholder ||maybe||
- Fixed sudoskill to use the new centralized player profiles for consistency
- Fixed ConcurrentModificationException with spawners saving during shutdown
- Fixed NPE when loading mob type with no display name
- Fixed case where `Despawn: false` mobs from a spawner would despawn anyway
- Fixed blockmask with variables again
- Fixed PhatLoots support not taking looting enchants into account
- Fixed ConcurrentModificationException with spawners when plugin is shutting down
- Fixed various issues with threat tables
- Fixed several saving issues when cloning a spawner
- Fixed looting issue with phatloot support
- Fixed various bugs with holograms and packet bullet culling
- Fixed custom nameplates not appearing for new players that join the server
- Fixed projectile velocity with text bullets
- Fixes to prevent spawner saving corruption
- Fix radius option on speak mechanic
- Fixed crashes involving mob bullets and orbitals
- 
- Added `bulletCullingDistance` option to display and text bullets
- Added `attackReachModifier` option to MeleeAttackGoal (defaults to 4)
- 
- 
- 




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


Older Changelogs
================
-   [5.4.X Changelogs](/5.4.x_changelogs)
-   [5.3.X Changelogs](/5.3.x_changelogs)
-   [5.2.X Changelogs](/5.2.x_changelogs)
-   [5.1.X Changelogs](/5.1.x_changelogs)
-   [5.0.X Changelogs](/5.0.x_changelogs)
-   [4.14.X Changelogs](/4.14.x_changelogs)
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