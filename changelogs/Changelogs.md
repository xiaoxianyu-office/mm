[[_TOC_]]

# 5.9.0 (Dev Builds)

Mechanics
---------
Add `specificStep/ss` to SlashMechanic

### NEW: `wait`
- New special keyword mechanic `wait`
- Will pause the skill tree until a condition is met


Targeters
---------
### NEW: `@PlayerLocationByName`

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

# 5.7.2
## General
- Added `ThreadPoolSize` option in `config-general.yml` to limit the number of async threads used by Mythic. Defaults to -1 (no limit).
- Added `toggleTimer` utility command.
- Added `-p` option to `spawner create` and `spawner move` commands, to create/move at the player's location.

## Mechanics
### Projectiles
- Upgraded MEG bullet type for projectiles.
- Added bullet-related options for MEG projectiles: `bulletScale`, `bulletColor`, `bulletGlowing`, `bulletGlowColor`.
### Variables
- Added `DOUBLE` variable type.

## Targeters
- Added `usePitch=true` option to `@EntitiesInCone` targeter.

## Random Spawners
- Allow placeholders in random spawner levels.

## Placeholders
Added <caster.type> and <caster.type.name> placeholders.

## Bugs / Other
- Added some new features to the `CustomComponentRegistry` API.
- Moved data tags for items to use PDC instead of NBT, fixing issues with Spigot deserialization on 1.21.
- Fixed a loading issue with parent stats.
- Fixed StackOverflowError that could occur with stats.
- Fixed broken parent placeholders.
- Fixed a calculation error in EntitiesInCone for range.
- Fixed missing caster placeholders and added c. aliases.
- Fixed entity_effect/mobSpell particle issues.
- Fixed NPE in BukkitItemStack.
- Fixed NPE in auras.
- Fixed NPE when signaling mobs from console.
- Fixed skill parameters not being passed to skills called by condition actions.
- Fixed empty lines in drop ChatMessages not showing up.
- Fixed a memory leak caused by usages of entity metadata.
- Fixed a bug with onSpawnOrLoad event not firing.
- Fixed error spam with particles introduced in previous builds.
- Fixed plugin not loading on 1.19.4.
- Fixed invalid particle data causing issues.
- Fixed y out-of-bounds error for max world height calculations.
- Fixed an issue with threat tables where NPE and calculation errors were occurring.
- Fixed the setName mechanic looping issue by changing <caster.name> to <caster.type.name>.
- Fixed issues with lootsplosions causing items to not stack.

# 5.7.1
## General
- Added 1.21.1 support

# 5.7.0

**`Note: 1.21 support was a huge upgrade and there may still be bugs. Please make sure to report any bugs you find by opening an Issue or by letting us know in the `mythic-121-testing` channel in Discord`**

## General
- Added 1.20.5, 1.20.6 and 1.21 support
- Dropped support for 1.16.4, 1.18.2, 1.19.1, 1.19.2, and 1.19.3.
- Various options on mobs and skills that take an item can now accept a droptable and will use a random item from it, such as the Item mob type.

## Mobs
- Added support for new entity types: `Armadillo`, `Bogged`, and `Breeze`.
- Added new HEARING ability to mobs enabled by `Hearing.Enabled: true`. Requires 1.20+
- Added [`~onHear`](/Mobs/Mobs#hearing) trigger that responds to hearing sounds
- Added `Options.PreventConversion` to zombies and skeletons.
- Changed variables defined directly on the mob default to always saving.

## Skills
### Mechanics
- Added particles: `white_smoke`, `dust_plume`, `gust`, `gust_emitter`, `gust_dust`, and `trial_spawner_detection`
- Particle `mobSpellAmbient` was removed by Mojang in 1.21
- Allow `command` and `message` mechanics to target locations for the purpose of location-based placeholders.
- Renamed `setItemDisplay` mechanic to `setDisplayEntityItem` to clarify purpose and avoid naming conflicts.

#### NEW: `Log`
- `log{message="Debug to console with variables <caster.var.test>"}`

#### NEW: `SetTextDisplay`
- `setTextDisplay{text="text here"} @Target`

#### NEW: `Taunt`
- Sets the caster's threat to 110% of the current target's target and forces them to attack the caster. Requires threat tables.

#### NEW: `openTrades`
- `openTrades (openTrade, trade)` mechanic to open a merchant menu to the targeted player.
- Added `realTrade/real` attribute - determines if the player trades with the actual villager or not (ie drop trade xp, etc.).

#### NEW: `setChunkForceLoaded`
- Sets the target location's chunk to be force-loaded

#### DropItem
- Added `then=` skill to the dropItem mechanic that targets the dropped item entities.

### Conditions
- Added `onPass[Skill]` & `onFail[Skill]` for conditions.

#### NEW: `boundingBoxesOverlap`

#### NEW: `distanceFromPin`
- `distanceFromPin{pin=X;distance=<5}`

#### NEW: `distanceFromLocation`
- `distanceFromLocation` condition. Values `x`,`y`,`z`,`distance/d`, and optional `world` (default to players current world if no world name provided).

### Targeters
#### NEW: `@BlocksInPinRegion`

#### NEW: `@HighestBlock`
- Targets the highest location at the origin position.

#### NEW: `@TrackedPlayers`
- Targets players that are within render distance of and currently rendering the mob

#### NEW: `@ChunksinWERegion`
- Added `@ChunksinWERegion{region=X}` targeter.

#### Pin
- Added `random=true` option, if targeting a multi-pin it will target a random one instead of all of them.

### Placeholders
- Added `PlaceholderBoolean` which will evaluate to true if a variable is 'true' or '1', otherwise false.
- Added rounding support to `random.float` placeholder by using syntax `<random.float.1to5{round=2}>`

API
----
- Refactored EquipSlots to allow for custom slots.
- Various API improvements for MythicRPG.
- Added methods for dumping item component data.

Bugs / Other
------------
- Improved world isLoaded check.
- Removed `type` alias for `damageType` in damage mechanics to fix some conflicts.
- Removed adventure shading, switched to using native adventure with spigot libraries loader.
- Removed redundant old version checks.
- Fixed bugs with rounding in stat tooltips in some cases.
- Fixed y out of range error with random spawning.
- Fixed setName mechanic not updating properly when using custom nameplates.
- Fixed NPE in papi variable placeholders.
- Fixed several NPEs when trying to resolve player variables before a player has finished loading in.
- Fixed several more bugs with placeholder rounding.
- Fixed attribute slots not working on some versions.
- Fixed colors not working in stat formatting.
- Fixed async error with threat table targeters.
- Fixed NoSuchElementException leading to server crash with random spawning on 1.21.
- Fixed NPE in dumpNBTData method on 1.21.
- Fixed `Spawners.DisableCommandSaving` logic being backwards.
- Fixed yaw and pitch attributes not saving on spawners.
- Fixed spawners not saving.
- Fixed a bunch of broken targeters.
- Fixed NPE in VariableManager.
- Fixed attack speed stat (hopefully).
- Fixed spread not working on teleport mechanic with entity targets.
- Fixed bug with item display entities.
- Fixed backwards compatibility with potions.
- Fixed Armor and Attack Speed not being able to be set to 0.
- Fixed errors related to EntityManager.
- Fixed a bunch of spam errors about registering entities.
- Fixed NPE with mob eggs that have no display name.
- Fixed piglin brutes being broken for vanilla overrides.
- Fixed some other vanilla override issues with babies.
- Fixed totem_of_undying particle.
- Fixed a bunch of particle bugs.
- Fixed default potion level being 2 instead of 1.
- Fixed fireworks loading colors with RBG instead of RGB.
- Fixed onDamaged aura not working with skill damage, probably.
- Fixed ClassCastException with compatibility mode.
- Fixed NPE with `targetInterval` mechanic option.
- Fixed spread not working on teleport mechanic with entity targets.
- Fixed summon mechanic mobs inheriting caster's yaw in certain situations.
- Fixed `hasPotionEffect` condition on 1.21.
- Fixed custom attribute registration on 1.21+.
- Fixed async error with threat table targeters.
- Fixed NoSuchElementException leading to server crash with random spawning on 1.21.
- Fixed custom attribute registration on 1.21+.
- Fixed y out of range error with random spawning.
- Fixed summon mechanic mobs inheriting caster's yaw in certain situations.
- Fixed piglin brutes being broken for vanilla overrides.
- Fixed some other vanilla override issues with babies.
- Fixed default potion level being 2 instead of 1.
- Fixed fireworks loading colors with RBG instead of RGB.
- Fixed onDamaged aura not working with skill damage, probably.
- Fixed summon mechanic mobs inheriting caster's yaw in certain situations.
- Fixed `hasPotionEffect` condition on 1.21.
- Fixed custom attribute registration on 1.21+.
- Fixed spread not working on teleport mechanic with entity targets.
- Fixed `setName` mechanic not updating properly when using custom nameplates.
- Fixed `consumeSlotItem` mechanic not removing items with 0 amount
- Fixed MythicMobItemGenerateEvent#setItemStack
- Fixed damage modifiers and defensive stats not working in some cases when the final damage is zero
- Fixed mob data not always saving on server shutdown
- Fixed meleeAttack AI goal causing zombies to stutter or freeze sometimes
- Fixed persistent entities not loading correctly after chunk load due to papermc bug
- Fixed error preventing plugin from loading on Arclight
- Fixed config error causing plugin to require a restart after first install

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