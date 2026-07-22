[[_TOC_]]

# 5.13.0

General
-------
- Added `PackDependencies` and `FileDependencies` to `packinfo.yml`, letting a pack declare which plugins/files it needs so Mythic skips (instead of parsing and erroring on) content gated behind a missing dependency
```yaml
PackDependencies:
- MythicCrucible
FileDependencies:
- enchantments/* MythicEnchants
```
- Spawners gained `Chance`, `RandomRotation`, and `UseWorldScaling` options; most spawner fields (`Cooldown`, `Warmup`, `MobsPerSpawn`, `MobLevel`, `Radius`, `RadiusY`, `ActivationRange`, `ScalingRange`, `LeashRange`) now accept placeholders and ranged values instead of only flat numbers
```yaml
Chance: 0.5
RandomRotation: true
Cooldown: 5to10
MobsPerSpawn: 1to3
```
- Numeric attributes across 40+ mechanics (`missile`, `projectile`, `beam`, `summon`, `orbital`, `lightning`, `shootfireball`, `volley`, `raytrace`, particle effect mechanics, and more) now accept placeholders instead of only static numbers
- Added `Hide`, `HideFlags`, `Glint`, and `Enchantments` icon options to menu configs; fixed conditionally-overridden icons showing item flags they shouldn't (#2232)

Stats
-----
- Changed `CRITICAL_STRIKE_DAMAGE` back to a compounding multiplier on final damage instead of being folded into the same additive pool as mechanics like `modifyDamage{}`
- Fixed a lost-update race in stat recompute that could drop concurrent stat changes (e.g. from async auras); health regen now reads the live stat value every tick instead of a cache that could desync

Mechanics
---------

### NEW: Cinematics System
- Added a scripted camera system for cutscenes, boss intros, and scripted reveals: keyframed camera paths are defined under `cutscenes/` (or inline) and played back for a player with the `cinematicCamera` mechanic (aliases `cinecam`, `camerapath`), supporting looping, per-leg easing curves, a packet-only `DISPLAY` camera or a `TELEPORT`-based fallback, and optional `onStart`/`onEnd` skills
- Added the `cinematicCancel` mechanic (aliases `cinecancel`, `stopcinematic`) to stop an active cinematic early
- Added the `isInCinematic` condition (aliases `incinematic`, `incine`, `cinematicactive`) and the `cinematic.active`, `cinematic.frame`, and `cinematic.progress` placeholders
- Added the `/mm camera <pathId> add|remove` command for building camera paths in-game
- Added `MythicCinematicStartEvent` (cancellable) and `MythicCinematicEndEvent` API events for addons
- Fixed the `DISPLAY` camera mode not loading chunks along the camera path

```yaml
my_path_id:
  duration: 100
  easing: EASE_IN_OUT_CUBIC
  points:
  - "world,100,70,100,90,10"
  - "~,0,5,-10,0,30,40"

- cinematicCamera{path=my_path_id} @target
```

### NEW: clearpath
- Added the `clearpath` mechanic (aliases `stoppath`, `clearnavigation`, `stopnavigation`), clearing the target mob's current navigation path

```yaml
- clearpath @self
```

### Mount Mode
- Added a `mode` option to the `mount` and `summonPassenger` mechanics: `ADD` (adds as a passenger), `SET` (sets the passenger, fails if one already exists, previous default behavior), or `REPLACE` (replaces all current passengers)

```yaml
- mount{type=Wolf;mode=ADD} @self
- summonPassenger{type=Horse;mode=REPLACE} @self
```

### OnDeath Aura Component
- Added a `ce`/`cancelEvent` option to the `ondeath` aura component: on a successful on-death skill (Paper only), the death event is now cancelled and the entity revived instead of dying

```yaml
- aura{onDeathSkill=ReviveSkill;ce=true} @self
```

### Aura Component cancelOn* Flags
- `cancelOnDeath`, `cancelOnCasterDeath`, `cancelOnTeleport`, `cancelOnChangeWorld`, `cancelOnGiveDamage`, and `cancelOnTakeDamage` can now be set on an individual aura component instead of only the aura line (#2254)

```yaml
- aura{auraname=Shield;duration=200;components=[
    - ondamaged{cancelOnTakeDamage=true;ondamaged=BreakShield}
  ]} @self
```

### Misc
- `setProjectileDirection` now supports entity-target dispatch (e.g. `@target`) in addition to location targets (#2229)
- Added `hitBlockConditions` (alias `hbcond`) to `missile`, `projectile`, and `slashProjectile`, letting conditions evaluated against the hit block decide whether the projectile is allowed to stop there
- The `forEach` mechanic now exposes the current loop index via `<skill.var.index>`
- The `delay` mechanic's `ticks` parameter now also accepts placeholders
- `aura` merging can now override the attachment of an already-running instance instead of always keeping the original
- Added the `firefly` particle type

Conditions
----------

### NEW: isCancelled
- Added the `isCancelled` condition (aliases `isCanceled`, `cancelled`, `canceled`), checking whether the triggering event is currently cancelled, e.g. after an earlier `cancelevent` in the same skill chain

```yaml
Skills:
- cancelevent{}
- message{m="blocked!"} ~onDamaged ?isCancelled
```

### NEW: skyLightLevel
- Added the `skyLightLevel` condition, testing the sky light level (light from the sky only) at the target location

```yaml
- skylightlevel{l=10}
```

### entityType Condition: Nested Variant Matching
- `entityType`/`mobtype` now accepts per-type constraints (`variant`, `color`, `style`, `mainGene`, `hiddenGene`, `biome`, `profession`, `crack`, `bodyColor`, `patternColor`, `pattern`) to match specific animal variants, villager professions/biomes, sheep/llama/shulker colors, iron golem crack state, tropical fish patterns, and more

```yaml
- entityType{type=[COW{variant=warm},SHEEP{color=rainbow}]}
- entityType{type=VILLAGER{profession=librarian;biome=taiga}}
```

### Misc
- Added a `shape` option (`SPHERE` default, `CYLINDER`, `SQUARE`) to `mobsInRadius`, matching the shape option already on the `EntitiesInRadius`/`EntitiesNearOrigin` targeters
- Added the `angry` condition (alias `isAngry`) for bees, wolves, and vexes
- Added the `pollinated` condition (aliases `isPollinated`, `hasNectar`) for bees
- Expanded `isSheared` to also check bogged and snowmen
- `variableContains` gained an `EXACT_ENTRY` (aliases `EXACTENTRY`, `EE`) compare type, matching a whole comma-separated entry instead of a substring
- `heightAbove`/`heightBelow` now resolve their `height` value with the casting skill's metadata, so it accepts skill variables and other placeholders
- Added the `inBounds` condition (aliases `withinBounds`, `insideBounds`); see `onEnterBounds` below

Targeters
---------

### NEW: targetinvulnerable
- Added the `targetinvulnerable` targeter option (default `true`); set to `false` to skip invulnerable entities (e.g. `Options.Invincible` mobs)

```yaml
@EntitiesInRadius{r=10;targetinvulnerable=false}
```

### mythic / vanilla Filters
- Added `mythic` and `vanilla` as `target`/`ignore` filter values, restricting a targeter to only Mythic entities or only non-Mythic (vanilla) ones

```yaml
@EntitiesInRadius{r=10;target=mythic}
@EntitiesInRadius{r=10;ignore=vanilla}
```

### NEW: Display/Interaction Target Filters
- Added `targettextdisplays`, `targetitemdisplays`, `targetblockdisplays`, and `targetinteractions` filters (all default `true`), letting skills include or exclude text/item/block display and interaction entities

### Misc
- The `uuid` targeter now accepts a comma-separated list of UUIDs instead of only one

Mobs
----

### NEW: Default Level
- Added a top-level `Level` mob option (aliases `MobLevel`, `Options.Level`) setting the mob's default level, used whenever it spawns without an explicit one (spawner, `/mm mobs spawn`, totem, mob bullet, etc); accepts a fixed value or a `minTOmax` range rolled per spawn
- Spawners with no `MobLevel` set now use the mob's own `Level` (or 1) instead of spawning level 0 mobs
- Negative `LevelModifiers` values now work (previously silently ignored), so a stat can decrease per level
- Mob level is never clamped below 1 anymore, including stray fractional levels from world scaling
- A mob's saved level is read back correctly on reload/chunk-reload instead of being guessed from health

```yaml
MyBoss:
  Type: ZOMBIE
  Level: 5
  LevelModifiers:
    HEALTH: 50
    MOVEMENT_SPEED: -0.005
```

### Misc
- Added `DefaultMobOptions.PreventJockeyMounts`, `PreventConversion`, `PreventLeashing`, `PreventItemPickup`, and `NoDamageTicks` global defaults in `config-mobs.yml`; fixed `DefaultMobOptions.PreventVanillaDamage` never being read

Triggers
--------

### NEW: onEnterBounds / onExitBounds
- Added mob triggers that fire when a mob crosses into or out of an axis-aligned box defined by two corners (checked on the mob's timer clock; a mob spawning inside fires `onEnterBounds` on its first check). Corners accept a pin name, `world,x,y,z`, or `x,y,z`, and support placeholders/math

```yaml
Skills:
- message{m="Entered the arena"} @World ~onEnterBounds{corner1=world,100,64,100;corner2=world,120,80,120}
```

Placeholders
------------

### NEW: min / max / clamp
- Added `.min{amount=X}`, `.max{amount=X}`, and `.clamp{min=A;max=B}` meta placeholders for bounding a numeric placeholder or variable inline, instead of `variableSet`+`variableInRange` chains

```yaml
- setvariable{var=caster.spawn_chance;value=<caster.var.spawn_chance.clamp{min=0;max=100}>} @self
```

### Misc
- Added `location.temperature` (aliases `l.temp`, `temp`), returning the adjusted biome temperature at a location
- Added `absorption` (alias `absorb`), returning the scoped entity's current absorption (golden) health
- `<skill.var.damage-type>` now falls back to the damage's tags (comma-joined) instead of the literal `SKILL` when no element is set; added `<skill.var.damage-tags>` for the raw tag list
- Added `slot.item`, returning the item in an entity's equipment/inventory slot as a drillable item value supporting item meta-keywords

Items
-----
- `BAG`-type items now default their stack size to 1 (still overridable via `Options.StackSize`)

API
---
- Added `MythicLoadedEvent`, fired once the plugin has fully finished loading
- Added `MythicCinematicStartEvent`/`MythicCinematicEndEvent` (see Cinematics System above)
- `MythicTriggerEvent` now implements `Cancellable`
- Added a `LootBag#give` overload taking a `BiFunction` so addons can override how drop items are added to a player's inventory
- Added a `LootBag#give` overload taking a `BiConsumer` for custom handling of items that don't fit in the player's inventory
- Fixed addon-registered placeholders being dropped when `MythicPlaceholdersLoadEvent` fired before the addon subscribed to it (#2214)
- Restored the deprecated `SkillCondition#evaluateLocation(AbstractLocation)` overload for addon compatibility

Compatibility
-------------
- Added support for Minecraft 26.2
- Improved Folia handling across triggers, spawners, mechanics, projectiles, and particle batching (region-thread dispatch for `altitude`, `DEATH`/death-observer, random spawn, spawner ticking, mechanic entity state, projectile `onHit`, and scheduler usage)
- Fixed `~onMount`/`~onDismount` throwing `NoClassDefFoundError` on 1.20.1
- Fixed `EntityKnockbackEvent` breaking plugin load on 1.20.4
- Fixed a snow golem entity-type lookup crash and guarded breeze projectile detection on pre-1.21

Bug Fixes / Other
-----------------
- Cached compiled math expressions in placeholders, conditions, and variable math for up to ~20x faster evaluation
- Reduced per-tick allocations in skill delay placeholders, targeters, and projectile packet dispatch
- Optimized packet-bullet rotation parsing, entity-teleport packets, AoE condition location resolution, and boss bar range checks
- Optimized player-movement tracking with a lock-free per-player location holder instead of cloning `Location` on every move event
- Reduced target-list copying in hot `SkillMetadata` clones
- Replaced chunk iteration with a direct AABB spatial query in `getEntitiesNearLocation`, with NaN/Infinite-coordinate guards and finite world-height bounds
- Made `VariableRegistry`/`PlayerVariableRegistry` lock-free and stopped firing `MythicPlayerVariableSetEvent` twice per bulk-write entry
- Reduced per-tick allocations across projectile, packet-render, and damage-trigger hot paths
- Kept `VariableRegistry`'s backing map a `ConcurrentHashMap` after Gson deserialization instead of rebuilding it as Gson's `LinkedTreeMap`
- Shared a single `WorldUnloadEvent` listener across all active projectiles instead of one per projectile
- Skipped allocating a knockback-resistance `AttributeModifier`/UUID per hit in `doDamage` unless actually needed
- Optimized the packet-entity renderer's per-tick player iteration and switched packet yaw/pitch to primitive storage
- Replaced Stream pipelines with plain loops in `ILocationSelector` filtering
- Removed throwaway list allocations in `PacketEntityRenderer.sendPacket`
- Cut projectile per-tick packet dispatch overhead and cached entity UUIDs during target evaluation
- Cut roughly a second off every `/mm reload` by caching jar annotation scans and skipping a per-item exception when no shield color is set
- Sped up `/mm reload` further by narrowing config lookup-cache invalidation to just the affected section
- Reduced per-tick target-evaluation overhead in projectile hit detection
- Reduced redundant block-state lookups during projectile collision checks
- Reduced allocations in projectile target buffering
- Optimized async combat skill dispatch (~1.9x faster)
- Optimized `CylinderShape`/`SquareShape` targeters, `altitude` condition, and `stun` mechanic location lookups; `onDamaged` aura matching no longer allocates a `HashMap` per hit
- Optimized `pin` targeter random picks and hoisted repeated lookups out of timer-skill and mob-clock loops
- Fixed O(n²) slowdown in `targetinterval` batching and `RandomRingPointTargeter` picks as target counts grow
- Fixed `particletornado`'s cloud particle sending invalid data and spamming "particle data is void" in console
- Fixed a NullPointerException in skill cooldown checks and mechanic dispatch when a caster's entity was null
- Fixed player-dropped items ignoring `DropGlowColor`/`DropBeamColor` (#2264)
- Fixed `chainmissile` never bouncing to new targets (#2287)
- Fixed `PreventSnowFormation` not applying during a snow golem's death animation (#2149)
- Fixed self-target damage mechanics being blocked when PvP is disabled (#2285)
- Fixed `hitbox`/`hitboxissubhitbox` conditions not seeing the ModelEngine sub-hitbox bone struck by a projectile
- Fixed the command-skill executor never initializing when only MythicRPG was installed
- Fixed `blockmask` masking only occluding blocks by default instead of all non-air blocks (#2277)
- Fixed dark hologram text and a concurrency NullPointerException in hologram rendering (#2199)
- Guarded `rayTraceBlock` against infinite/NaN or extremely distant coordinates that could hang the server
- Fixed the `attack_cooldown` placeholder and `~onAttack` trigger reading the post-reset cooldown value on 26.1+ (#2257)
- Fixed a memory leak where projectile bookkeeping used entity metadata instead of persistent data, leaking until server restart
- Fixed `~onHear` never reacting to projectile sounds (arrows, thrown potions, etc.)
- Fixed `bulletKillable` projectiles terminating on their first hit instead of only on death or despawn (#2272)
- Fixed the `stat` aura component losing its applied modifier on `/mm reload` (#2271)
- Fixed `ARROW` projectile bullets dealing shield-bypassing vanilla arrow damage alongside the intended skill damage (#2274)
- Fixed mobs keeping vanilla random equipment when their chunk unloaded before the deferred equip pass ran
- Fixed `recoil`'s `pitch`/`yaw` options not resolving placeholders/math expressions per cast (#2265)
- Fixed disabled stats not loading their display/formatting config, which NPE'd Crucible item lore generation
- Fixed `~onBowHit` not firing for Crucible's simulated projectile skill damage (#2261)
- Fixed the `damage` mechanic's re-entrancy guard dropping onAttack-triggered damage even with `triggerSkills`/`ts=true` set (#2269)
- Fixed attribute-mapped stat changes (e.g. from async aura ticks) applying off the entity's owning thread and corrupting the attribute tracker (#2270)
- Fixed `hugSurface`/`heightFromSurface` on the `totem` mechanic not actually positioning the model (#2267)
- Fixed orbital `bullet=DISPLAY` rendering off its circular path due to a forward offset (#2237)
- Fixed the `DamageModifier` stat's `TriggerStats`/`ParentStats` reading from the wrong stat's config scope (#2213)
- Fixed `dialog` element/button conditions being evaluated against the caster instead of the viewer, buttons ignoring their own conditions/cooldown, and dialogs not reloading on `/mm reload` (#2251)
- Fixed the `sound` mechanic's `volume` not supporting placeholders
- Fixed the `metaskill` mechanic evaluating its target skill's Conditions twice per cast (#2246)
- Fixed random-spawn `maxHeight` not being bounded to the world's build height limit (#2260)
- Fixed a Model Engine model being applied twice on spawn when `Model.Id` was configured
- Fixed duration fields (e.g. `Cooldown`, mechanic durations) losing the ability to be given as a random range after duration units were added
- Fixed the `speak{}` mechanic's speech-bubble hologram rendering dark
- Fixed `tracklocation` and other location-targeted mechanics silently doing nothing when cast with an entity targeter
- Fixed the `onDeath` aura component not firing on player deaths
- Fixed the `onDeath` aura component never firing when `cancelOnDeath` was enabled
- Fixed spawner warmup not arming when the async despawn clock finalized a kill as a despawn before the death event arrived (#2204)
- Guarded entity teleports against unloaded/null worlds, including the `teleport` mechanic and a projectile's end skill on world unload
- Fixed `recoil`/`fear` forced rotation kicking players with "Invalid move player packet received"
- Fixed the `charged`/`creeperCharged` condition failing to load due to a constructor mismatch
- Fixed generated `tooltip_style` component keys not resolving under the MythicCrucible pack namespace
- Fixed damage modifiers that reduce entity vs entity damage to exactly 0 not applying unless `CancelDamageIfZero` was also enabled
- Fixed a race between the async mob clock and `EntityDeathEvent` that could skip the `DEATH` trigger or miss a killer's `PreventMobKillDrops` on quick deaths
- Fixed `shoot` mechanic's `ITEM` and `BLOCK` projectile types not working
- Fixed `blockwave` throwing `LIGHT` blocks

# 5.12.1

General
-------
- Particle effects are now queued and bundled to greatly reduce packet usage, and particle effects will not respect the client's particle settings (configurable)
- Added support for using duration units in skill cooldowns and most mechanics with durations and intervals by adding a suffix (e.g. `5s` = 5 seconds, `20t` = 20 ticks)
```yaml
Cooldown: 5t
Cooldown: 1m

- potion{type=POISON;duration=10s}
```

Stats
-----

### NEW: MUTATOR Stats
- Added the `MUTATOR` custom stat type for applying a stat value to other stats through components, formulas, and operations

```yaml
AGILITY:
  Enabled: false
  Type: MUTATOR
  AlwaysActive: true
  Display: 'Agility'
  PlayerBaseValue: 0
  Components:
    - Stat: BONUS_DAMAGE
      Formula: 'v / 5'
      Operation: ADDITIVE
    - Stat: CRITICAL_STRIKE_CHANCE
      Formula: 'v / 1000'
      Operation: ADDITIVE
```

Command Skills
--------------

### Command Parent
- Added `Command.Parent` to command skills to allow for creation of sub-commands.

```yaml
ParentCommandSkill:
  Command:
    Id: parent

ChildCommandSkill:
  Command:
    Id: child
    Parent: ParentCommandSkill
```

Mechanics
---------

### OnAttack Aura Component
- Added trigger condition support to the `onattack` aura component

```yaml
- aura{auraname=Counter;duration=200;components=[ - onattack{onattack=CounterSkill} ]} @self ?targetwithin{d=5}
```

### ToggleSitting
- Added the `togglesitting` mechanic for controlling pet sitting

```yaml
- togglesitting{state=toggle} @target
- sit{state=true} @target
```

Conditions
----------

### NEW: canBeHitByProjectile
- Added the `canBeHitByProjectile` condition
- Custom MEG hitboxes are skipped through the API

```yaml
- canBeHitByProjectile
- hitByProjectile
```

### NEW: petsitting
- Added the `petsitting` condition for checking whether a pet is sitting

```yaml
- petsitting
- petsit
```

Triggers
--------

### NEW: onEffectRemove
- Added the `onEffectRemove` trigger

```yaml
Skills:
  - skill{s=EffectRemovedSkill} ~onEffectRemove
```

Items
-----

### CustomModelData Component
- Added support for typed `CustomModelData` component values
- Supports `float`, `string`, `boolean`, and `color` data
- Supports scalar, list, and map-list formats
- Requires Paper 1.21.4+

```yaml
CustomModelData:
  - float/1,2,3
  - string/example_model
  - boolean/true
  - color/#ff8800
```

API
---
- Exposed stat registration methods for addons
- Added `MythicStatsRegistrationEvent`
- Added `PlaceholderDuration`
- Added experimental API for packet item lore

Bug Fixes / Other
-----------------
- `incombat` can now check players tracked by the combat-tag tracker
- Improved Folia handling for `RandomSpawnGenerator`
- Improved Folia handling for `SetTextDisplayMechanic` entity writes
- Improved caster scheduling for virtual casters
- Optimized MythicMenu rendering by skipping per-render placeholder resolution for static placeholders
- Optimized text pixel length calculation
- Cached regex metakeyword patterns
- Optimized boss bar updates
- Optimized single-token placeholder parsing
- Optimized random location target selection
- Optimized final damage calculation
- Optimized spawner clock ticking
- Optimized target condition evaluation allocations
- Optimized random generation in `ChanceCondition`
- Optimized drop hot paths
- Optimized `EntitiesNearbyTargeter`
- Optimized `PlaceholderInt` parsing
- Optimized `IEntitySelector` player filtering
- Optimized variable string joins
- Optimized `MapVariable`, `MapSerializer`, and `AuraRegistry` loops
- Fixed `blockwave` to use the existing `BlockState` when no material is specified
- Fixed `setDisplayEntityItem` nt supporting block display entities
- Fixed some issues with default stat base values in `stats.yml`
- Fixed `sortNum` placeholder output for list variables
- Fixed `sortNum` placeholder output for set variables
- Fixed documented defaults not being honored in `playersInRadius`
- Fixed MiniMessage tags not parsing in custom kill messages
- Fixed default flash particles not being colored white
- Fixed overlapping `blockmask` mechanics with durations so newer masks keep their duration when older masks expire
- Fixed `RandomSpawner` `REPLACE` recursion on Mythic-initiated spawns
- Fixed `hasitem` defaulting amount to the condition variable instead of `>0`
- Fixed nameplate brightness
- Fixed stat executor loading order
- Fixed parent command handling for command skills
- Fixed `stats.yml` extraction timing so addons can register stats early
- Fixed `particlelineequation` ignoring `eqy` and `eqz`
- Fixed `teleport` losing `preservepitch` and `preserveyaw` during safe spawn lookup
- Fixed `particlesphere` applying `yoffset` twice
- Fixed `trail` particle location key using the source instead of the target
- Fixed `aura{cancelOnDeath=false}` persisting through player respawn
- Fixed `MythicMobDeathEvent` and drops being missed during async skill clock races
- Fixed 1.21.1 compatibility issues
- Fixed inverted `BukkitAttribute.values()` filtering
- Fixed `onTick` auras continuing after expiry
- Fixed negative-duration aura loops
- Fixed nested entity targeters in `location=` slots not applying sort, conditions, or limit
- Fixed `onattack` skill variables for `damage-amount`
- Fixed `onattack` skill variables for `damage-type`
- Fixed `onattack` skill variables for `damage-cause`
- Fixed `MobsNearOrigin` throwing an NPE when type is missing
- Fixed `MobsNearOrigin` to log a config error when type is missing
- Fixed `pickupitem` leaving fancy-drop PDC on picked-up items
- Fixed `giveitem` filling decorated pots instead of dropping items beside them
- Fixed summoning issues
- Fixed durations returning excessive precision
- Fixed math formulas returning excessive precision
- Fixed `damage{}` not respecting `triggerSkills`
- Fixed `stun` allowing players to teleport upward
- Fixed `stun` restoring `g=` as an aura group option
- Fixed `-1` not giving infinite duration on potions

# 5.12.0

General
-------
- Added support for 1.21.11 and `26.1.x` (requires Java 25)
- Added automatic config updating
- Improved case-insensitive config loading
- Added new `files/` pack directory
- Added auto-generated `.internal` pack. This will contain some assets that can be auto-generated by Crucible, along with other helpful internal things that can modified.

Stats System
------------
- Updated the default `stats.yml` with better base values
- Added missing stats to the default `stats.yml`
- Added `LOOT_BIAS` stat for affecting weighted droptables

Mechanics
---------

### NEW: Aura Components
- Rewrote auras to be component-based so a single aura can combine multiple effects
- Added `targetIsCaster=true`
- Added `decayStackOnExpire=true`
- Added persistent `cancelOnQuit=false`
- Added `ChunkLoadAuraComponent`
- Added `projectilerebound`

```yaml
- aura{auraname=MultiAura;duration=200;interval=10;targetIsCaster=true;decayStackOnExpire=true;components=[ - onattack{onattack=[ - particles{p=flame;a=50;s=1} @self ]}, - stat{stat=HEALTH;type=ADDITIVE;value=20} ]} @target
```

### NEW: removeTaggedAuras
- Added `removeTaggedAuras` for clearing aura instances by tag

```yaml
- removeTaggedAuras{tags=stun;limit=2} @target
```

### NEW: Charges / CooldownMode
- Added `Charges` to skills and metaskills
- Added `CooldownMode` to skills and metaskills

```yaml
Charges: 3
CooldownMode: PARALLEL
```

### NEW: addSkillCharges
- Added `addSkillCharges` for restoring charges to tracked skills

```yaml
- addSkillCharges{skill=Dash;amount=1;order=LATEST;overflow=true} @self
```

### NEW: showDialog
- Added `showDialog` for opening custom Paper dialogs

```yaml
- showDialog{dialog=QuestOffer} @trigger
```

### NEW: closeDialog
- Added `closeDialog` for force-closing an active dialog

```yaml
- closeDialog @trigger
```

### NEW: hide
- Added `hide` / `hideFromPlayers` for hiding the caster from targeted players, with optional persistence

```yaml
- hide{permanent=true;save=true} @PlayersInRadius{r=30}
```

### NEW: enchantItem
- Added `enchantItem` for applying enchantments directly to a target slot

```yaml
- enchantItem{enchant=SHARPNESS;level=1;slot=HAND} @self
```

### NEW: SetCustomMenuTitle
- Added `SetCustomMenuTitle` / `setMenuTitle` for updating an open custom menu title

```yaml
- setMenuTitle{title="<gold>Boss Rewards"} @self
```

### Wait
- Added `onTimeoutSkill` / `ontimeout` / `ots` to `wait`

```yaml
- wait{cond=[ - onground ];tt=300;ontimeout=TimeoutSkill}
```

### Sudo
- Added `chained=true` to `sudo`

```yaml
- sudoskill{chained=true;skill=Example} @EIR{limit=3;radius=10}
```

### Heal
- Added `tags` to heal mechanics

```yaml
- heal{a=10;tags=holy,burst} @self
```

### DropItem
- Added `ForceDynamic` to `DropItem`

```yaml
- dropitem{item=MyDrop;ForceDynamic=true} @self
```

### Sound
- Added `emitter` and `seed` options to sound mechanics

```yaml
- sound{s=minecraft:entity.warden.heartbeat;emitter=caster;seed=42} @self
```

### Projectile
- Added `spread` to `volley`
- Added `bulletBrightness` to projectile mechanics
- Added `bulletALOD=false` to projectile mechanics

```yaml
- volley{spread=4} @target
```

### Throw
- Added placeholder support and `triggers=false` to `throw`

```yaml
- throw{v="<caster.var.throw_speed>";vy=1.5;triggers=false} @target
```

### Custom Menus
- Added `Shared: false` to custom menus
- Added `UIElements` to custom menus

```yaml
CustomMenu:
  Shared: false
  UIElements:
  - myc_menu_hats{char=\ue832;path=ui/cosmetics_gui_hat;height=256;ascent=14}
```

Conditions
----------

### NEW: input
- Added `input` for checking live player movement keys

```yaml
- input{key=forward,sprint}
```

### NEW: skillIsRecharging
- Added `skillIsRecharging` for checking skill recharge state

```yaml
- skillIsRecharging{skill=Dash}
```

### NEW: statDamageModifier
- Added `statDamageModifier` for stat skill checks

```yaml
- statDamageModifier{m=1.01} castInstead PositiveEffectSkill
```

### NEW: inLiquid
- Added `inLiquid`, including waterlogged block support

```yaml
- inLiquid
```

### NEW: isFrozen
- Added `isFrozen`
- Added `freezing` / `isfreezing` aliases

```yaml
- isFrozen
```

### NEW: uuid
- Added `uuid` for comparing an entity against a specific UUID value

```yaml
- uuid{u="<trigger.uuid>"}
```

### NEW: goatHorn
- Added `goatHorn` for checking whether a goat still has a horn

```yaml
- goatHorn
```

### NEW: isSheared
- Added `isSheared` for checking sheep shearing state

```yaml
- isSheared
```

### NEW: trim
- Added `trim` / `armorTrim` for checking armor trim pattern and material

```yaml
- trim{slot=CHEST;pattern=sentry;material=gold}
```

### NEW: blockAbove
- Added `blockAbove` for checking material at an offset above the evaluated location

```yaml
- blockAbove{m=DIRT;y=2}
```

### NEW: isTarget
- Added `isTarget` / `target` for checking whether the evaluated entity is the caster mob’s current target

```yaml
- isTarget
```

### inClaim
- Extended `inClaim` support to PlotSquared
- Extended `inClaim` support to Residence

```yaml
- inClaim
```

### Composite Conditions
- Composite conditions may now contain spaces more reliably

```yaml
- ((day false || raining true) && onBlock{material=LIME_CONCRETE}) true
```

### Item Filters
- Added placeholder support to `hasitem`
- Added variable support to `hasitem`
- Added placeholder support to `haspermission`
- Added variable support to `haspermission`
- Added runtime item filter resolution to item-related conditions and mechanics

```yaml
- hasitem{i="<caster.var.required_item>"}
```

Targeters
---------

### useBoundingBox
- Added `useBoundingBox` / `bb=true` to shaped entity targeters and cone bounding-box checks for `@EIC`

```yaml
@EIC{a=45;r=12;bb=true}
```

### sort
- Added `sort=OLDEST` and `sort=NEWEST` for entity target filters

```yaml
@EIR{r=20;sort=OLDEST}
```

### EntitiesInLine
- Added placeholder + math support to `EntitiesInLine` radius

```yaml
@EntitiesInLine{r="<skill.var.beam_radius>"}
```

### RandomLocations
- Added placeholder + math support to `RandomLocations` targeters

```yaml
@RandomLocations{a=5;r="<caster.var.scatter_radius>"}
```

Mobs
----

### NEW: 1.21.11 Entity Types
- Added support for `CAMEL_HUSK`
- Added support for `NAUTILUS`
- Added support for `PARCHED`
- Added support for `ZOMBIE_NAUTLIS`

```yaml
Type: CAMEL_HUSK
```

### NEW: Axolotl Variant
- Added `Variant` support for Axolotls

```yaml
Variant: blue
```

### ThreatTable
- Added `ThreatTable.DropUnreachableSeconds`

```yaml
ThreatTable.DropUnreachableSeconds: 10
```

### Saddles
- Added newer mob support to saddle logic
- Improved `isSaddled` support for newer mobs

```yaml
- isSaddled
```

Triggers
--------

### NEW: Input Triggers
- Added `~onInputForward`
- Added `~onInputBackward`
- Added `~onInputLeft`
- Added `~onInputRight`
- Added `~onInputJump`
- Added `~onInputSneak`
- Added `~onInputSprint`

```yaml
- message{m="Jump detected"} ~onInputJump
```

### NEW: onHealed
- Added `~onHealed`

```yaml
- skill{s=AfterHeal} ~onHealed
```

### NEW: onSheared
- Added `~onSheared`

```yaml
- skill{s=AfterShear} ~onSheared
```

### NEW: onEffectApply
- Added `~onEffectApply`

```yaml
- skill{s=OnPotionGain} ~onEffectApply
```

### NEW: onThrownByMechanic
- Added `~onThrownByMechanic`, with `~onThrown` as an alias

```yaml
- skill{s=AfterThrow} ~onThrown
```

### NEW: onMount
- Enabled `~onMount`

```yaml
- skill{s=MountedSkill} ~onMount
```

Placeholders
------------

### Placeholder Engine
- Refactored placeholders onto a new parser/segment pipeline
- Added wildcard registration
- Added generic return types
- Added `MythicLineConfig` support for meta keywords
- Improved static placeholder parsing
- Added `{default=...}` support to variable placeholders

### NEW: Input Placeholder
- Added live input placeholders for player movement state

```text
<trigger.input.jump>
```

### NEW: Aura Stacks Placeholder
- Added `<caster.aura.ID.stacks>`

```text
<caster.aura.FireShield.stacks>
```

### NEW: <skill.power>
- Added `<skill.power>`

```yaml
- message{m="Power: <skill.power>"} @self
```

### NEW: Skill Charge Placeholders
- Added `<[scope].skill.SkillName.charges>`
- Added `<[scope].skill.SkillName.maxcharges>`
- Added `<[scope].skill.SkillName.overflowcharges>`

```yaml
- message{m="Dash: <caster.skill.Dash.charges>/<caster.skill.Dash.maxcharges> (+<caster.skill.Dash.overflowcharges>)"} @self
```

### NEW: damage-amount-post
- Added `damage-amount-post`
- Added `<skill.var.damage-amount-post>`

```yaml
- message{m="Final damage: <skill.var.damage-amount-post>"} @self
```

### NEW: Dialog Placeholders
- Added dialog input placeholders

```yaml
- message{m="Class: <dialog.classChoice>"} @trigger
```

### NEW: itemcount
- Added `itemcount` for counting vanilla or Mythic items in a player's inventory

```yaml
- message{m="Diamonds: <caster.itemcount.DIAMOND>"} @self
```

### NEW: <char.*>
- Added `<char.*>` for deferred Unicode character insertion

```text
<char.007B>
```

### NEW: Random UUID
- Added `<random.uuid>`

```yaml
- message{m="<random.uuid>"} @self
```

### Misc
- Added `sortByValue` map meta keyword
- Added `round` math support
- Renamed `<item.level>` to `<item.droplevel>`

Items
-----

### General
- Added `Options.Glint: false` support

### New Component Support
- Added `AttackRange`
- Added `BlocksAttacks`
- Added `Weapon`
- Added `KineticWeapon`
- Added `PiercingWeapon`
- Added `JukeboxPlayable`
- Added `NoteBlockSound`
- Added `UseRemainder`
- Added `BreakSound`
- Added `Instrument`
- Added `Enchantable`
- Added `RepairableBy`
- Added `OminousBottleAmplifier`
- Added `PotDecorations`
- Added `banner_patterns`
- Added `LodestoneTracker`

```yaml
AnItem:
  Material: DIAMOND
  AttackRange: 3.5
  Weapon:
    ItemDamagePerAttack: 2
    DisableBlockingForSeconds: 0.5
  JukeboxPlayable: "minecraft:thirteen"
  UseRemainder: ADifferentItem
  RepairableBy:
  - STICK
  PotDecorations:
    Back: brick
    Left: arms_up_pottery_sherd
    Right: skull_pottery_sherd
    Front: prize_pottery_sherd
```

API
---
- Added API for registering custom command functions
- Added API for custom equippables
- Added `MythicPlayerQuitEvent`
- Added `MythicAuraStartEvent`
- Added `MythicAuraStopEvent`
- Added `MythicMobPreSpawnConfigureEvent`
- Added `MythicTargetEvent`
- Added final attack meta damage interception API
- Exposed aura remaining ticks
- Added menu hooks
- Added icon hooks
- Added color-picker hooks

Compatibility
-------------
- Greatly improved Folia compatibility
- Added `inClaim` support for PlotSquared
- Added `inClaim` support for Residence

Bug Fixes & Optimizations
-------------------------
- Refactored the placeholder engine
- Improved static placeholder handling
- Reduced hot-path allocations in projectiles
- Reduced hot-path allocations in targeters
- Reduced hot-path allocations in drops
- Reduced hot-path allocations in cooldowns
- Reduced hot-path allocations in clustering
- Reduced hot-path allocations in registry lookups
- Improved menu reload performance
- Improved custom-name component caching
- Optimized case-insensitive config handling
- Fixed persistent aura save/rejoin issues
- Fixed aura termination races
- Fixed `removeAura` stat leaks
- Fixed `onDamaged` aura regressions
- Fixed random placeholder output regressions
- Fixed MiniMessage placeholder regressions
- Fixed bar placeholder regressions
- Fixed stance placeholder regressions
- Fixed threat-table placeholder regressions
- Fixed cached stat placeholder regressions
- Fixed static placeholder regressions
- Fixed non-placeholder `<` parsing issues
- Fixed recursive placeholder cache races
- Fixed placeholder concurrency issues
- Fixed negative projectile gravity
- Fixed projectile hits against owner sub-hitboxes
- Fixed text display brightness issues
- Fixed zero-velocity display bullets
- Fixed projectile bounce axis bugs
- Fixed projectile NPEs
- Fixed `doEndSkillOnHit=false` handling
- Fixed random spawning logic
- Fixed spawner stale data
- Fixed per-player random spawn cooldowns
- Fixed double spawns
- Fixed natural despawn unregistering
- Fixed persistent mob restore on chunk load
- Fixed level scaling issues
- Fixed `BaseValue` stat issues
- Fixed stat rounding issues
- Fixed heal percent issues
- Fixed additive damage modifier behavior
- Fixed `modDamage{action=ADD}` applying damage as a multiplier
- Fixed item attribute doubling and reload resets
- Fixed `OnCooldownSkill` redirects ignoring the target skill cooldown
- Fixed menu generation issues
- Fixed conditional menu issues
- Fixed menu reload performance issues
- Fixed hidden item handling
- Fixed FAWE schematic lookup outside Mythic folders
- Fixed `EntitiesInCone` targeting when looking up or down
- Fixed `haspotion` condition issues
- Fixed `inLiquid` condition issues
- Fixed summon owner/parent flags
- Fixed `runaigoal` priorities and stacking
- Fixed hologram hex colors without Nexo
- Fixed additional `26.1.x` follow-up issues
- Fixed Folia chunk races
- Fixed Folia command races
- Fixed Folia potion effect threading issues
- Fixed Folia visibility threading issues
- Fixed Folia heal event threading issues
- Fixed Folia totem handling
- Fixed Folia trading handling

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
- [Meta Variable Placeholders](/Skills/Placeholders/meta-placeholders): `<[scope].var.[name].keyword>` with keyword chaining
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