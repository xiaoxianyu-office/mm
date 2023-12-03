5.4.5
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

5.4.0
=====

Highlights
----------
### Version support
Added support for 1.20.2

### Damage
- Added support for multi-type damage
- Added DamageTags, allowing you to specify any number of arbitrary tags on any damage mechanics using tags=THIS,THAT e.g. `- damage{amount=5;tags=FIRE}`
- Added `damageTag` condition, checks if the damage that triggered the skill has the given tag
- Changed element damage attribute to just apply a damage tag

### Projectile Upgrades
- Projectile Tick-Interpolation
- Added DISPLAY and TEXT bullet types
- Item Display Bullet Type: Add "tx", "ty" and "tz" (t from translation) to offset the visual position of the bullet, also "translation"("pos", "offset") to set all the values at the same time in the x,y,z format
- Added `bulletBrightness`, and `bulletBrightnessBlock` + `bulletBrightnessSky` for some reason to Display bullets
- Added `bulletBillboard` to Display bullets
- Added `bulletForwardOffset` to mob bullets
- Added `bulletCullingDistance` option to display and text bullets

### Stat System
- Added the [Stat System](/Stats)

### Holograms
- Added our own hologram system
- All hologram-related features no longer require a 3rd party hologram plugin
- Made it so mob names can be multi-line using nameplates feature on 1.19.4+ using `\n` for newlines

### Spawners
- Major spawners rewrite - see spawners section

General
-------
- Added `/mm test mechanic [line]` command to test executing a skill line
- Allow CustomModelData in `packinfo.yml`
- Upgraded the item editor with a bunch of new buttons

Mobs
----
- Added support for mobs having players as parents

Added new mobs types:
- `BLOCK_DISPLAY`
- `CAMEL`
- `CHEST_BOAT`
- `ITEM_DISPLAY`
- `SNIFFER`
- `TEXT_DISPLAY`

### AI
- Added `radius` option to `LookAtPlayers` goal
- Added `attackReachModifier` option to MeleeAttackGoal (defaults to 4)

Mechanics
----------

### NEW: Cancel
- Cancels the current skill tree

```yml
SomeSkill:
 Skills:
 - message{m="hello"} @server
 - cancel ?isMonster #cancels the rest of the skill from executing
 - message{m="bye"} @server
```

### NEW: Hit
- Simulates a physical hit from the caster using their damage attribute, held weapon, etc
- Same options as `baseDamage` mechanic
- Takes melee stats into account (regular skill damage won't unless configured to specifically)

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

### NEW: `setProjectileBulletModel`
- Added `setProjectileBulletModel{model=X}` mechanic, can be called by a projectile to change the bullet's item's model ID (only works with DISPLAY bullets)

### NEW: `StatAura`
- Applies a stat modifier to the target as an aura. 

Example:
```
- stataura{stat=PARRY_CHANCE;type=ADDITIVE;value=0.5;duration=200} @self ~onDamaged
```
- would increase the caster's parry chance stat by 50% for 10 seconds when damaged

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

### Switch
- Allow to run MetaSkills & Code Refactor

### Rally
- Rewrote Rally mechanic. Added `conditions` option to rally, and all attributes are now optional.

### Volley
- Add "pickup"/"canPickup" attribute, defaults to true

Conditions
----------

### NEW: DamageTag

Added damageTag condition, checks if the damage that triggered the skill has the given tag

`- damageTag{tag=FIRE}`

### NEW: directionalVelocity

- Added `directionalVelocity` condition, which checks if the target has a velocity matching the given parameters.
- Added side, forward and vertical aliases to DirectionalVelocityCondition

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

### NEW: MaterialOnCooldown
`materialIsOnCooldown` condition, aliases `materialCooldown`, `matCooldown` 
arguments `material` / `mat` / `m`, defaults to enderpearl

true if material type is on cooldown for the player, false otherwise

### NEW: SpawnReason

Audiences
---------
- Added TRACKED audience, which are the players that are rendering the caster on their client

Placeholders
------------

### General
- Added `<caster.stat.STAT_NAME>` placeholders
- Added `<target.block.data>` - returns the block data of a block
- Added `<target.item.type>` placeholder
- Added placeholder support for variable name in all variable mechanics

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
- Added placeholder support to a bunch of new things
- Updated some of the default configuration files to be more up to date
- Refactor some skill tree stuff
- Merge ExtendedDamageMetadata into DamageMetadata
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
- Fixed an issue with DisplayTransformationMechanic
- Fixed `DisplayOptions.Block` for block_display entities
- Fixed non-string Crucible NBT placeholders not returning their value
- Fixed NPE in PlaceholderStringImpl
- Fixed Multi-Templates to be read on the correct order (Left to Right)
- Fixed onAttack and onDamaged executing with power=0 instead of power=1
- Fixed bugs with arrow bullets
- Fixed offset option not working on speech bubbles
- Fixed SetRotation just completely borked
- Fixed DamageModifiers and HealthBars being broken on recent versions
- Fixed Display bullet orientation on 1.20+
- Fixed inconsistencies with ProjectileVelocity mechanic when relative=true
- Fixed `config.yml` not generating on new servers
- Fixed and tested variable saving for all the different scopes
- Fixed variable duration not calculating expiration time properly
- Fixed bullets and several other errors on the orbital mechanic closes #1310
- Fixed fov condition's rotation attribute not working closes #1298
- Fixed tadpoles closes #1304
- Fixed some errors with damage calculation closes #1295
- Fixed NPE when using an mmoitem in a holding condition closes #1291
- Fixed various issues with DamageModifiers
- Fixed NPE in PotionClear mechanic
- Fixed weird inconsistency with zombified piglin vanilla overrides
- Fixed intersection error with projectile bouncing
- Fixed itemSpray items being able to be picked up by hoppers
- Fixed @FloorOfTargets meta-targeter not working with location targets
- Fixed NPE in Rally mechanic
- Fixed `KillMessagePrefix: ''` not disabling the kill message prefix
- Fixed the "-p" flag for the killall command
- Fixed NPE in listactive command
- Fixed NearbyAudience checking for targets that might be in different worlds
- Fixed `CAST` condition action executing multiple times
- Fixed `zombified_piglin` not recognized as a valid mob type closes #1319
- Fixed SwitchMechanic not working for some conditions
- Fixed HasOffhandCondition to check for other living targets instead of only players
- Fixed EjectPassengerMechanic being called async
- Fixed particles to use nearby audience by default instead of world, reducing RX
- Fixed `relative` option in VelocityMechanic. Now acts similar to projectileVelocity.
- Fixed KillCommand not removing non-living mythicmobs
- Fixed raytrace mechanics running async from auras


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