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