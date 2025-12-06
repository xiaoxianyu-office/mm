[[_TOC_]]

# 5.10.0 (Release)

## General
- Added **1.21.7** and **1.21.8** support
- Added `HAPPY_GHAST` entity type
- Performance: faster second-pass processing and improved caching for entity lookups and item parsing on reload
- Default config: added several missing options

## API & Events
- New: `MythicReloadCompleteEvent`
- New (core): `ReloadEvent`
- New: `MythicPlayerVariableSetEvent`, `MythicPlayerVariableRemoveEvent`
- `MythicHealMechanicEvent` now also calls `EntityRegainHealthEvent`
- Added meta access to `DamageMetadata`
- Added old meta access in `SkillTriggerMetadata`
- Added API groundwork for RPG cross-compatibility

## Placeholders
- Added `<target.armor>`, `<&lt>`, `<&gt>`, `<^dot>`, `<^dot2>`
- Added `PlaceholderAngle`
- Placeholders now supported in more places (e.g., item browser parsing)
- Fixed generic `int`, `float`, and `double` placeholders not parsing variables
- Fixed PlaceholderVector not working under complex cases
- Fixed placeholders with Item NBT (string/int/float/double) not resolving

## Variables
- New variable types: `Set`, `List`, `Map`, `Boolean`, `Vector`, `Time`, **Item**, **MetaSkill**
- [Meta Variable Placeholders](/Skills/Placeholders#meta-variable-placeholders): `<[scope].var.[name].keyword>` with keyword chaining
- `Variable.ofType` updated; `PolymorphicPlaceholder` added
- Mob Variables can set all registered variable types
- Internals: relocated Default Variable handler for Crucible usage

## Mechanics
- **New**: [`ForEach`](/Skills/Mechanics/ForEach) and [`ForEachValue`](/Skills/Mechanics/ForEachValue)
- **New**: `ClearTarget` mechanic
- Updated: `variableadd` / `variablesubtract` to support new variable types
- Projectile family:
  - Added many missing projectile options
  - Added `startYOffset`, `startForwardOffset`, `startSideOffset` to `shoot` and `volley`
- Orbital family:
  - Added placeholder support to `ParticleOrbital` radius
  - Added `immuneDelay`; fixed multi-hit immunity
  - Removed `hs` alias for `hugSurface`
  - Improved targeting logic with orbitals
- Aura: `sync=true` now forces sync scheduler
- Look mechanic: minor behavioral tweaks
- Summon: fixed `useTargetYaw`/`useTargetPitch`
- Stun: fixed `freezeFacing` inversion; fixed on newer versions

## Teleport (Paper-only)
- **Added** options to all teleport mechanics (Paper):
  - Teleport cause
  - Vehicle retention
  - Support for Paper `TeleportFlag`s
- Fixes: addressed regressions that broke teleport mechanics; additional polish to new options

## Targeters & Triggers
- Targeters:
  - Added `shape` to `@EntitiesInRadius` and `@EntitiesNearOrigin`
  - Added universal `upoffset` location attribute
- Triggers:
  - Shulkers now support `onShoot` and `onBowHit`
  - Fixed `onDeath` for falling block mobs

## Conditions
- **New**: [`VariableContains`](/Skills/Conditions/VariableContains)
- **New**: `projectileHasEnded`
- **New**: `isSkill{name=...}`
- `mythicMobType` condition: `exactmatch=false` option
- Added `xdiff` and `zdiff` conditions
- Fixed health conditional parsing triggers

## Items & Equipment
- Item flags: allow full flags (e.g., `HIDE_ATTRIBUTES`) in `Hide` field
- Compatibility: drop unsupported `HIDE_POTION_EFFECTS` on > 1.20.5
- Item systems:
  - Faster item cache on reload (also parses placeholders/variables)
  - Fixed tool rules (closes #2027)
  - Fixed cases where item mechanics could fail
  - Attempted fix for `vanillaonly=true` in `ItemMatcher`

## Mobs & Spawning
- Options:
  - `Options.Aware: false`
  - `Options.PreventKnockback`
  - `Hidden: true` (prevents mobs appearing in lists) and fixed inheritance making it useless
- Datapacks: proper spawn location for mobs spawned by datapacks

## Holograms & Displays
- Holograms: fixed multiple regressions in previous builds
- Text display bullets:
  - Added `bulletRotation`
  - Fixed rotation code on 1.20_R1

## Compatibility & Misc

## Bug Fixes & Other
- Added placeholder support to summon radius attributes
- Fixed NPEs: startup (#2029), `MythicConfig`, `ForEach`, `Summon`, vector with `DisplayItem` totems, target setting
- Fixed recoil mechanic on 1.21.4+
- Fixed errors when other plugins call certain methods before load
- Fixed auras `IllegalStateException` introduced in a dev build
- Fixed level modifier errors (rare cases)
- Fixed `Log` mechanic message parsing
- Fixed `variableequals` warnings when target variable absent
- Fixed `onShoot` aura not setting `<skill.var.bow-tension>`
- Fixed various missile `verticalOffset` issues
- Fixed immutable list errors with glow on 1.21.8
- Fixed `setOwner`/`removeOwner` for all tameable types

# 5.9.5

Bug Fixes
---------
- Updated some dependencies
- Fixed items with attributes not stacking when they should
- Fixed certain durability-related things not using data from the new durability components
- Fixed some errors with level modifiers
- Fixed several issues with recoil effect on newer versions
- Fixed the freezeFacing option for the stun mechanic being inverted

# 5.9.4

Bug Fixes
---------
- Added `ignoreEntities` for raytraceTo mechanic
- Fixed `ignorePassable=false` in raytrace mechanics phasing through barrier blocks 

# 5.9.3

Bug Fixes
---------
- Fixed some issues with ignoreSameFaction target filter

# 5.9.2

General
-------
- Added `teleportToWorld=true/false` to `GoToOwner/Parent` AI Goals.
- Add "goal/g" aliases to runaitargetselector so they match the error message
- Added `%mythic_stat_...%` papi placeholder
- Added `<target.distanceSq>` and `<trigger.distanceSq>` placeholders

Conditions
----------
### NEW: CompareValues

Bug Fixes
---------
- Fixed suicide mechanic not counting the mob as damaging itself closes #1584
- Fixed speech bubbles having yaw/pitch inverted on newer versions
- Fixed MountMe mechanic maybe
- Fixed MapList elements not working for configured item NBT
- Fixed IllegalArgumentException with vanilla loot table drops closes #1949
- Fixed error with mob types with copying mob spawners closes #1951
- Fixed error in shield mechanic closes #1955
- Fixed NPE in `<skill.targets>` placeholder closes #1961
- Fixed ClientboundSetEntityDataPacket error on 1.21.4
- Fixed ops being put into every faction in the PermissionFactionProvider
- Fixed StackOverflowError on non-english servers
- Fixed plugin not loading when a menu icon is misconfigured

# 5.9.1

Bug Fixes
---------
- Fixed VariableMath mechanic not supporting double variables
- Fixed some bugs with ItemMatcher
- Fixed moveTowardsTargetConditional AI goal
- Fixed bouncing projectiles
- Fixed several other issues with projectiles
- Optimized projectiles that don't have hit skills
- Fixed `Options.Color` not working on potions
- Fixed error where projectiles with insanely high velocity could crash the server
- Fixed raytrace error on 1.21.5
- Fixed custom damage stats not triggering onDamaged auras
- Fixed `hitself` not working on projectiles

# 5.9.0

General
-------
- Added `/pins regionRedefine` command.
- Changed pack icons to use Mythic item syntax.
- Scaling Equations and `LevelModifiers` can now work with any stats.
- Added step and lerp functions to all numeric placeholders

```
step(e, x) { 0, x < e; 1, x >= e
lerp(a, b, r)
```

Mechanics
---------
### NEW: swingOffhand
- Added `swingOffhand` mechanic.

### NEW: setEntityPose
- Added `setEntityPose{pose=X}` mechanic.

### NEW: setItemGroupCooldown
- Added `setItemGroupCooldown{group=namespace:key;ticks=20}` mechanic.

### Hit
- Added `scaleByAttackCooldown` to hit mechanic (scales damage based on weapon attack cooldown).

### Leap
- Noise now defaults to `0` on the `Leap` mechanic.

### MetaSkill
- Added `snapshotStats=true` to `MetaSkill` mechanic.

### Missile
- Added `startWithParentVelocity` option to `missile` mechanic.

### Projectiles
- Added HitTargeter to projectile type mechanics

hitTarget htr accepts an entity targeter. Entities targeted by htr would be processed through onHit and gain immune delay

### Slash
- Add `specificStep/ss` to SlashMechanic

### Totem
- `faceAwayFromCaster=true` option added to Totem mechanic.
- `hugSurface=true` option added to Totem mechanic.

### Wait
- New special keyword mechanic `wait`
- Will pause the skill tree until a condition is met

Conditions
----------

### NEW: itemGroupOnCooldown
- Added `itemGroupOnCooldown{group=namespace:key}` condition.

### NEW: Server Version Conditions
- Added `serverAfter{version=1.21.4;inclusive=true}`, `serverBefore{version=1.21.4;inclusive=false}`, and `serverIsPaper` conditions.

### Stance
- Changed default `strict` value to `true` for the `stance` condition.

Targeters
---------
- Fixed several bugs with `@FloorOfTarget` targeter.
- Changed default `faulty=false` for location selector option.
- Added `relative=true/false` to `@RingAroundOrigin` targeter.

### NEW: `@PlayerLocationByName`
### NEW: `@PredictedTargetLocation`
`@PredictedTargetLocation{ticks=X}`
- Targets the predicted location of the caster's target in the next X ticks based on their velocity

Triggers
---------
- Renamed `onTridentHit` to `onProjectileHit`, `onTridentThrow` to `onProjectileThrow`.
- Added `onProjectileLand` trigger.

Placeholders
------------
### NEW: Distance Placeholders
- Added `<target.distance>` and `<trigger.distance>` placeholders.

### NEW: Epoch Placeholders
- Added `<utils.epoch>`, `<utils.epoch.millis>`, and `<utils.epoch.ticks>` placeholders.

Items
-----

### Vanilla Loot Table Drop
- Added new drop type `- vanillaLootTable minecraft:table_name` to drop items from vanilla loot tables and data packs.

### BlockStates Component
- Added support for `BlockStates` component to specify block states on items:
  ```yaml
  TestBlockStates:
    Material: OAK_SLAB
    Display: 'Waterlogged Slab'
    Options.Placeable: true
    BlockStates:
    - type top
    - waterlogged true
  ```

### Glider Component
- Added `Glider: true` option to items to implement the Glider component.

### UUID & Timestamp Options
- Added `Options.GenerateUUID: true/false` and `Options.GenerateTimestamp: true/false` to assign a UUID or timestamp to items on generation.

API
---
### NEW: Event Methods
- Exposed event methods.
- Added `MythicSkillEvent` when a skill is called.

### NEW: Crucible & RPG API
- Exposed API for Crucible and RPG features.

### NEW: Packet Display Entities API
- Exposed more API methods for packet-based display entities.

### NEW: Threat Table API
- Exposed threat table map.

### REMOVED: Deprecated Equipment Slot Method
- Removed super-old deprecated method of referencing equipment slots by slot number.

### AI Goals
- Upgraded `ownerTarget` and `ownerAttacker` AI goals to be used by any mob; added `parentAttacker` and `parentTarget` AI goals.
- Refactored owner interfaces for consistency.

Bug Fixes & Optimizations
-------------------------
- General refactoring and internal cleanup.
- Fixed terminable `onTerminate` skill not working in some cases.
- Fixed logic bug with projectile target filters.
- Fixed various mob options not applying since refactor.
- Fixed several bugs arising from stats refactor.
- Fixed API `get` method for max stack size.
- Fixed `IllegalArgumentException` in `ItemMatcher`.
- Fixed `NoSuchMethodError` with projectiles on 1.21.5.
- Fixed bugs in new pet AI features.
- Fixed async error in `MythicSkillEvent`.
- Fixed initial display packet bullet rotation not being used when spinning.
- Fixed an error occurring when a player joins on 1.21.5.
- Fixed MEG bullets on totems not rotating with the spawning entity.
- Fixed NPE with drops introduced recently.
- Fixed breakage with drop weights.
- Fixed last build breaking equipment.
- Fixed Nexo drops not working in equipment.
- Fixed equippable component applying even on pre-1.21.3 versions.
- Fixed certain blocks not working with block‐based bullets.
- Fixed `swingArm` mechanic on newer versions.
- Fixed multiple errors when loading custom mechanics.
- Fixed `MythicProvider` being registered too late in some cases.
- Fixed typo in `PreventStingerLoss` option.
- Fixed issues with `scaleByAttackCooldown` when hitting multiple targets.
- Fixed several bugs with `@FloorOfTarget` targeter.


# 5.8.2
## Bug Fixes / Other

- Optimized Packet Entities
- Optimized Projectiles
- TargetSelf will now ignore all other filters
- Removed some minor error logging
- Fixed ENO including caster regardless of condition when targetself = true
- Fixed HitTargeter on projectiles
- Fixed some custom AI goals not loading since a few updates ago
- Fixed some issues with the item matcher and associated mechanics
- Fixed particles throwing errors on 1.20.X versions
- Fixed ClassCastException in item tool rules
- Fixed MountTarget mechanic being broken on newer versions
- Fixed NPE in StatExecutor
- Fixed threat tables tracking threat even if damage was cancelled
- Fixed threat not using final damage amounts after stats, damage modifiers, etc
- Fixed FancyDrops damage tracking not tracking projectile or skill damage
- Fixed FancyDrops not using final damage amount after stats, damage modifiers, etc when calculating contributions
- Fixed FancyDrops damage calculations and leaderboards taking cancelled damage into account
- Fixed case where death leaderboards wouldn't show for all players involved
- Fixed terminated reference always being cloned
- Fixed varequal and varrange not using skill meta
- Fixed stat not using base value on startup
- Fixed varinRange condition not being able to reference skill variables as a TargetCondition
- Fixed NPE in @ThreatTablePlayers targeter

# 5.8.1

General
-------
- Added missing particles `infested`, `block_crumble`, `trail`
- Added missing vanilla attributes as stats: 
  - BLOCK_BREAK_SPEED
  - BLOCK_INTERACTION_RANGE
  - ENTITY_INTERACTION_RANGE
- Added `then=` skill option to `dropItem` mechanic
- Added `then=` skill option to `remove` mechanic
- Added Placeholder support for `radius` in `MobsInRadiusTargeter`
- Allow message mechanic to be used without target

Bug Fixes / Other
-----------------
- Optimizations for menus
- Refactor & cleanup Template System 
- Removed some stray debugging
- Fixed lifesteal stat being backwards
- Fixed some issues with health regen stat
- Fixed ConcurrentModificationException in SkillMechanic
- Fixed some bugs with templates
- Fixed branched metaskills being canceled with terminable
- Fixed projectile rotations during the first tick for the shoot mechanic
- Fixed metadata deep clone not cloning targets by value
- Fixed console spam about magic values




Older Changelogs
================
-   [5.10.X Changelogs](/changelogs/5.10.x_changelogs)
-   [5.9.X Changelogs](/changelogs/5.9.x_changelogs)
-   [5.8.X Changelogs](/changelogs/5.8.x_changelogs)
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