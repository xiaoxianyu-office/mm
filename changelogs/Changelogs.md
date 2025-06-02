```
[[_TOC_]]

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

# 5.8.0

**`Note: This update includes various optimizations, new mechanics, improvements, bug fixes, and additional API features. Please report any issues you find by opening an Issue or letting us know in the appropriate Discord channel.`**

General
-------
- Added 1.21.3 and 1.21.4 support
- Lots of micro-optimizations for performance (thank you, Taiyou!)
- Added `Configuration.General.AnnounceOpReload` to `config-general.yml` to set whether Mythic reload announcements are sent to all online operators.
- Optimized various projectile/entity selection mechanics and removed stream usage in key areas (e.g., `IEntitySelector`, `PacketEntityRenderer`).
- Added a global option to automatically apply FancyDrops to all items (disabled by default).
- Added `/mm m spawn [type] [amount] @targeter` command.

Random Spawning
---------------
- **Multiple Mobs with Weights**: You can now specify multiple mobs in a Random Spawner entry with weighted values, for example:
  ```yaml
  Deeps:
    Types:
    - RegularZombie 100
    - BigZombie 50
    - GiantZombie 5
    Worlds: world
    Chance: 0.1
    Priority: 1
    Action: ADD
    PositionType: LAND
  ```
- **Structures Support**: Added a `Structures:` list option allowing you to limit a Random Spawner to spawn mobs only in specific structures:
  ```yaml
  Nether_Fortress:
    Types:
    - blaze_wisp 100
    Worlds: world_nether
    Chance: 0.02
    Priority: 1
    Action: ADD
    PositionType: LAND
    Structures:
    - 'minecraft:fortress'
    - 'incendium:forbidden_castle'
  ```
- **New Config Options**:
  - `RandomSpawning.MaxGenerationAttempts` to limit how many attempts the cluster generator tries when spawning.
  - `RandomSpawning.LocalSpawningLimit` and a new `MaxLocalMobs` option on individual Random Spawners to override local limits.
- **Renamed**: The old `GroupMultiplier` option is now `LocalGroupMultiplier` in `config-spawning.yml`, and its default value logic has changed.
- Various improvements to cluster generation and structure detection logic.

Mobs
----
- Streamlined variant options to `Options.Variant` for wolves, cats, frogs, villagers, etc., allowing for custom variants.
- Added ability to configure **custom mob spawner items**, including the ability to set spawn delay, spawn range, etc.
- Added Wolf-specific `Options.Variant` for custom wolf variants.

Mechanics
---------

### `NEW: followPath`
- An aura causing the target mob to walk along a defined path.

### `NEW: log`
- `log{message="Debug to console with variables <caster.var.test>"}` for simple logging.

### `NEW: setTextDisplay`
- `setTextDisplay{text="text here"} @Target` mechanic for displaying text.

### `NEW: openTrades`
- Opens a merchant menu for the targeted player.
  - `realTrade/real` attribute determines if trades are with a real villager.

### `NEW: movePin`
- `movePin{pin=X}` mechanic to relocate pins.

### `NEW: directionalVelocity`
- `directionalVelocity{yaw=50}` applies velocity to the target based on specified angles.

### `NEW: rotateTowards`
- Rotates the caster toward the target.

### `NEW: setChunkForceLoaded`
- Force-loads a chunk at the target location.

### `NEW: resetAI`
- Reverts a mob’s AI to factory defaults.

### `NEW: matchRotation`
- `matchRotation{of=@targeter}` to match rotation of a given target.

### `NEW: clearExperience`
- Resets a player's experience points.

### `NEW: setProjectileDirection`
- `setProjectileDirection{magnitude=1}` for controlling projectile direction.

### `NEW: lookAtTarget`
- An AI goal causing a mob to look at its current target.

### `UPDATED: dropItem`
- Now includes a `then=` skill section targeting dropped items.

### `UPDATED: setSpeed`
- Respects the configured movement speed; defaults to mob's base if none is set.

### `UPDATED: consumeSlotItem`
- Properly removes items with `0` amount.

### `UPDATED: shoot`
- Now supports `item=<material>` for custom projectiles (e.g., `item=REDSTONE`).

### `UPDATED: particleOrbital`
- Terminates after the caster dies/despawns and supports placeholders for `ticks`.

### `recoil`
- Fixed recoil on 1.21+; placeholders can be used in recoil values.

Conditions
----------

### `NEW: boundingBoxesOverlap`
- Checks if bounding boxes overlap.

### `NEW: distanceFromPin`
- `distanceFromPin{pin=X;distance=<5}` condition.

### `NEW: distanceFromLocation`
- `distanceFromLocation{x=...;y=...;z=...;distance=...;world=...}` condition.

### `NEW: PlaceholderBoolean`
- True if a variable is 'true' or '1', otherwise false.

### `NEW: originDistanceFromPin`
- Checks distance from a specific pinned location.

### `NEW: stringEmpty / stringNotEmpty`
- Checks if a string is empty or not.

### `lookAt`
- Now has `distance`/`d` attribute (defaults to 5) to check if a mob is looking at a target within that distance.

Targeters
---------

### `NEW: @BlocksInPinRegion`
- Targets blocks within a pin-defined region.

### `NEW: @HighestBlock`
- Targets the highest block at the origin position.

### `NEW: @TrackedPlayers`
- Targets players currently rendering or tracking the mob.

### `NEW: @ChunksinWERegion`
- `@ChunksinWERegion{region=X}` targeter.

### `NEW: @PNO`
- Alias for `PlayersNearOrigin`.

### `NEW: @OwnerLocation`
- Targets the owner location of a tamed entity.

### `NEW: @ParentLocation`
- Targets the parent location.

### `NEW: @WolfOwner`
- Re-added targeter that selects the owner of a tamed wolf.

### `skipTargetsUpToIndex`
- Lets targeters skip the first N matched targets.

### `@ObstructingBlock`
- Rewritten for better performance.

### `mobsInRadius`
- Now properly detects vanilla mob types.### Placeholders
- Added rounding support to `random.float` placeholder with syntax `<random.float.1to5{round=2}>`.
- Added new math functions: `todegree(value)`, `toradian(value)`, and `clamp(value,min,max)`.
- **NEW:** `caster.attack_cooldown` placeholder for vanilla swing cooldown.

Items
-----
- Added `Options.Glint: true` to add the enchantment glint effect.
- Added Mythic color picker for customizing color-related item properties.
- Added `vfxmodel/vfxitemmodel` support for Fancy Drops using 1.21.3+ item models.
- Added `namespace:enchant_name` support in the `Enchantments` option.
- Added `strict=true` to all item conditions/mechanics to prevent matching Mythic items with vanilla items.
- Extended `Equippable` component to support additional fields.
- Added `#tag` and `*wildcard` support to `itemType` condition.
- Added `Tool` and `UseCooldown` sub-components for more item customization.
- Reordered item components so `TooltipStyle` loads last.

### NEW: `TooltipStyle` component for advanced item tooltips.
### NEW: `Consumable` component:
  ```yaml
  Item:
    Consumable:
      ConsumeSeconds: 5
      HasParticles: true
      Animation: SPEAR
      Sound: entity.chicken.egg
  ```

### NEW: `Food` Component
- Added Food components for items, enabling the creation of edible items:
  ```yaml
  NetheritePops:
    Material: NETHERITE_SCRAP
    Display: 'Delicious Scraps'
    Food:
      Nutrition: 2
      Saturation: 2
      EatSeconds: 2
      CanAlwaysEat: true
      Effects:
      - regeneration{duration=60}```

Stats
-----
- Added new Mythic Stats for the latest Minecraft attributes:
  - `STEP_HEIGHT`
  - `ARMOR`
  - `ARMOR_TOUGHNESS`
  - `BURNING_TIME`
  - `EXPLOSION_KNOCKBACK_RESISTANCE`
  - `FALL_DAMAGE_MULTIPLIER`
  - `GRAVITY`
  - `JUMP_STRENGTH`
  - `KNOCKBACK_RESISTANCE`
  - `MOVEMENT_EFFICIENCY`
  - `OXYGEN_BONUS`
  - `SAFE_FALL_DISTANCE`
  - `SNEAKING_SPEED`
  - `WATER_MOVEMENT_EFFICIENCY`

API
---
- Refactored `EquipSlots` to allow for custom slots.
- Added API methods for dumping item component data (e.g., `DropTable.usesWeights()`, `DropTable.GetDrops()`).

- Added API condition type `ISkillMetaLocationComparisonCondition`.
- Enhanced item matching with `BukkitItemMatcher`.
- Exposed more plugin triggers and event calls for custom expansions.

## Bug Fixes & Optimizations
- Pre-generate and store default mob attributes for faster performance on spawn.
- Improved world checking to fix some concurrency issues.
- Improved rounding with placeholders.
- Fixed random spawning mobs occasionally spawning in walls or negative coordinates.
- Fixed plugin failing to load on older versions when building for new.
- Fixed NPE with placeholder doubles in certain situations.
- Fixed `onPrime` trigger for creepers.
- Fixed custom blocks not working as mob totem heads.
- Particle effects no longer limited by Spigot’s default view range incorrectly.
- Fixed `force=true` option with `look` mechanic.
- Fixed negative gravity on projectiles.
- Fixed recoil on 1.21+.
- Fixed spawners not saving correctly and reversed logic in `Spawners.DisableCommandSaving`.
- Fixed `onDamaged` aura not triggering with skill damage.
- Fixed `consumeSlotItem` failing with item amounts of `0`.
- Fixed default potion level being `2` instead of `1`.
- Fixed fireworks color loading with `RBG` instead of `RGB`.
- Fixed `teleport{unsafe=false}` not placing players properly on a solid block.
- Fixed `hasItem`, `holding`, and other item conditions to support new item matcher.
- Fixed health regen stat incorrectly healing dead players.
- Fixed MythicDamageEvent for entities that cannot be damaged (canceled properly).
- Fixed `mobsInRadius` failing with certain vanilla types.
- Fixed spawner items not applying correct mob data.
- Fixed sub-hitbox metadata manipulations causing stack overflow.
- Fixed `spin` effect so it stops if caster is dead.
- Fixed IllegalArgumentException in `EnderBeam` mechanic.
- Fixed `setDisplayEntityItem` mechanic not working properly with Crucible-generated items.
- Fixed item display interpolation/rotation issues.
- Fixed mobs without `MovementSpeed` becoming stuck when using the `setSpeed` mechanic.
- Fixed `setSpeed` mechanic to now base multiplier on the mob type’s default speed if no config value.
- Fixed `chicken jockey` option not working.
- Fixed various boat types being broken on 1.21.4.
- Many additional concurrency and caching fixes (faster item lookups, distanceSquared, etc.).

This release includes many new features, bug fixes, and optimizations. If you encounter any issues or unexpected behavior, please report them in the appropriate channels!



Older Changelogs
================
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