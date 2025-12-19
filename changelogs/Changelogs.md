[[_TOC_]]


# 5.11.0

General
-------
- Added support for 1.21.10  
- Dropped support for 1.19.X, 1.20.2, 1.20.6, and 1.21.3  
- Kept support for 1.20.1, 1.20.4, 1.21.1, and 1.21.4+  
- Rewrote `/mm i import` and improved import of NBT, display, and MiniMessage lore  
- Moved most custom menu logic into the base plugin; menus now require Premium or RPG  
- Moved custom command handling from RPG into Premium  

Optimiations
------------
- Added `ShareComponents` option to deduplicate identical mechanics, targeters, and conditions  
- Optimized placeholder and component memory usage via flyweighting  

Compatibility
-------------
- Improved model application timing to further reduce flickering  
- Updated Lands support to the latest version  
- Updated LibsDisguises integration, disguising mobs before spawning to reduce flickering  
- Removed mcstats.org reporting  
- Disabled ShopGUIPlus support temporarily  

Mechanics
---------

### NEW: fear
- Added `fear` aura mechanic causing targets (including players) to run around uncontrollably  

### NEW: TRAIL particle
- Added `TRAIL` particle with `color`, `duration`, and `source=@targeter`  

### NEW: forEachPin
- Added `forEachPin{pin=X;skill=Y}` for executing a mechanic once per pin location  
- The active pin location is exposed via `@Pin`  

### NEW: VariableMove
- Added `VariableMove` mechanic to move variables across names/registries, with optional `createnew`  

### NEW: determineCondition
- Added `determineCondition` mechanic for dynamic condition evaluation in metaskills  

### Velocity
- `velocity` mechanic no longer alters components that are not specified  
- Recoil movement smoothed further  

### Misc
- Stun mechanic now defaults to type `#stun`  
- `blockwave` now uses the target block’s material when unspecified  
- Added `inheritExpirationTime` to `VariableMove`  
- Improved projectile hit detection against sub-hitboxes  

Conditions
----------

### NEW: MetaskillCondition
- Added `MetaskillCondition` to let metaskills determine condition results  

### NEW: isSibling
- Added `isSibling` condition to check sibling mob relationships  

### Targets Condition
- `targets` condition may now specify a targeter instead of relying on inherited targets  

### Enhancements
- Placeholder support added to `TargetWithin` and `TargetNotWithin`  
- Metaskill conditions may now parse skill parameters  
- Added error catching to `BlockType`  

Targeters
---------

### NEW: @EscapeLocation
- Added targeter that finds a nearby Enderman-like escape location  

### NEW: @EntitiesNearPin
- Added targeter for entities around a pin location  

### Location Targeters
- Added `surface` and `surfaceTolerance`  

Mobs
----

### NEW: Copper Golem (1.21.10)
- `Options.WeatheringState`  
- `Options.Waxed`  

### NEW: Mannequin (1.21.10)
- `MannequinOptions.Immovable`  
- `MannequinOptions.Description`  
- `MannequinOptions.Pose`  
- `MannequinOptions.Skin`  
- `MannequinOptions.Cape`  
- `MannequinOptions.Elytra`  
- `MannequinOptions.Model: CLASSIC/SLIM`  
- `MannequinOptions.Player`  

### Other Mob Additions
- Added `Options.Variant` for cow, chicken, and pig  
- Added `Options.RandomizeProperties` to disable vanilla random mob variation  

Triggers
--------

### NEW: onDismounted
- Added trigger for when an entity is dismounted  

Placeholders
------------

### Numeric Placeholder Improvements
- Added `Long` variable type  
- Added `.round` and `.precision.X` meta keywords  

### Static Placeholder Optimization
- Added static placeholder pre-parsing  
- Improved runtime performance and post-reload caching  

### Misc 
- Added experimental `<centertext>` placeholder  

Items
-----
- Added `ItemVariable` drop type for item-handling mechanics  
- Improved `/mm i import` handling of NBT and MiniMessage content  
- Added `Options.SkinID` for head items  
- Changed item version format to `major.minor.patch` (up to 255.255.255)  
- Added `drop:` prefix for item variables 

API
---
- Added RandomDouble bias (API-only)  
- Added icon template API for custom menus  
- Expanded templated menu icon functionality  
- Added more placeholder/variable APIs and RandomDouble bias configuration
- Try to append Mythic Type before spawning so that it's available in CreateSpawnEvent


Bug Fixes & Optimizations
-------------------------
- Added placeholder support to projectile gravity  
- Added placeholder support to bonus damage fields  
- Added `bonusDamageModifiers/bdm` to damage mechanics  
- Improved BlockMatcher error handling  
- Fixed mob spawn reason incorrectly being `PATROL`  
- Fixed vanilla overrides overwriting mob options on chunk reload  
- Fixed owner and parent AI goals on newer versions  
- Fixed `~onSpawnOrLoad` not firing when no `~onSpawn` triggers existed  
- Fixed multiple particle issues on newer versions  
- Fixed projectile inaccuracy at extreme coordinates  
- Fixed projectile sub-hitbox detection  
- Fixed aura attachments not being removed when expired  
- Fixed aura errors and concurrency issues on Folia  
- Fixed numerous Folia regressions (projectiles, auras, delays, summoning)  
- Fixed item attribute stacking issues  
- Fixed player heads on 1.21.10  
- Fixed invalid Base64 skull textures by auto-padding  
- Fixed NPEs in meta skills, drop-table-less mobs, and onKnockbackEntity  
- Fixed various BlockMatcher issues and improved error logging  
- Fixed import command failing on non-Paper servers  
- Fixed config loading issues caused by missing newline  
- Fixed placeholder spam and stat placeholder timing issues  
- Fixed recoil mechanic issues  
- Fixed debug spam from meleeattack goal  
- Fixed damage breaking in prior build  
- Fixed look mechanic on no-AI entities  
- Fixed skull-texture crashes in mob types  
- Fixed plugin not loading on 1.21.10  
- General refactoring and internal cleanup across systems



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
- [Meta Variable Placeholders](/Skills/Placeholders/meta-variable-placeholders): `<[scope].var.[name].keyword>` with keyword chaining
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