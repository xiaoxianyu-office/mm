5.0.0
======

**Highlights**
----------
- Mythic API separated out into an independent module (for add-on authors)
- Major API rewrite
- Registering custom triggers



4.13.0 (formerly 5.0.0-alpha1)
======

**Highlights**
----------
- 1.17.1 Support
- Removed 1.13, 1.14, and 1.15 support
- Added inline false conditions using ?! 
- Added inline trigger conditions using ?~
- Added inline false trigger conditions using ?~!
- Bunch of new mechanics and conditions
- A million bug fixes 

General
-------
- Added 1.17.1 Support

Mobs
----
- Added AXOLOTL
- Added GLOW_SQUID
- Added GOAT
- Added MARKER

Changed Despawn option, now accepts TRUE, FALSE, CHUNK, or PERSISTENT. 
- CHUNK will despawn mobs when they enter an unloaded chunk, but not when
players aren't nearby.
- PERSISTENT mobs will not despawn ever and will not be killed by `/mm m killall`

Mechanics
---------
### NEW: disguiseAsBlock
### NEW: Freeze
Freezes the target for [duration] number of ticks, like when players are stuck in powdered snow.
### NEW: giveItemFromSlot
### NEW: onBlockBreak
- Aura mechanic that triggers when the entity breaks a block
### NEW: hideFromPlayers
- Hides the caster, if the caster is a player, from other players for a set duration.
### NEW: trackLocation
- Sets the caster's "tracked location", which can be referenced with the @TrackedLocation targeter or the distanceFromTrackedLocation condition
### Particles
Fixed some inconsistencies with particles when specifying direction: 
- If direction is explicitly set, particles will now spawn at the target
location normally
- If direction is not explicitly set, particles will continue spawning
at the origin and move towards the target as before
### SudoSkill
- Added target override option to sudoSkill mechanic

Effects
-------
### New Particles
- drippingDripstoneLava, drippingDripstoneWater, dustColorTransition,
electricSpark, fallingDripstoneLava, fallingDripstoneWater, Glow,
glowingInk, Light, reversePortal, Scrape, snowflake, SmallFlame, vibration, waxOff,
waxOn

Targeters
---------
### General
- Added length mutator to location targeters
- Added origin=true option to @BlocksInRadius targeter
### NEW: @BlocksInChunk
### NEW: @BlocksNearOrigin
### NEW: @ForwardWall
### NEW: @ItemsInRadius
### NEW: @ItemsNearOrigin
### NEW: @NearestStructure
### NEW: @SelfEyeLocation
- has alias of EyeDirection for MME compat
### NEW: @SpawnLocation
### NEW: @TargetedLocation
### NEW: @TargetedTarget
### NEW: @TrackedLocation
### NEW: @UniqueIdentifier
### Forward
- Added rotation
### TargetLocation
- Added ignoreTransparent
### Ring
- Supports placeholders
### PlayersInRadius
- Supports placeholders
### EntitiesInRadius
- Supports placeholders


Custom AI
----------
### NEW: fleeFaction

Conditions
----------
### NEW: color
```
  Conditions:
  - color{c=RED}
```
### NEW: dimension
```
  Conditions:
  - dimension NETHER
```
### NEW: distanceFromTrackedLocation
### NEW: playersinRadius
```
  Conditions:
  - pir{amount=>5;r=10}
```
### NEW: hasitem
```
  Conditions:
  - hasitem{i=STICK;amount=2}
```
### NEW: isLeashed
### NEW: motionX, motionY, motionZ
### Biome
- Added exact=false option to biome condition
### BlockType
- Now supports mmoitems blocks
### Holding
- Now supports MythicMobs and MMOItems items. For MMOItems, use `mmoitems.TYPE.ID` for the material/item attribute.
### Wearing
- Now supports MMOItems. For MMOItems, use `mmoitems.Type.ID` for the material/item attribute.

Spawners
--------
### Added Pitch and Yaw options

Items
-----


Placeholders
------------
- Added <target.entity_type>
- Added <target.block.type>
- Added <skill.targets>
- Added <target.l.yaw>
- Added <target.l.pitch>
- Added <trigger.l.yaw>
- Added <trigger.l.pitch>
- Added <target.level>
- Added <caster.damage>

Compatibility
-------------
- Updated to latest FAWE for fawePaste

### GriefPrevention
- Added inClaim, nearClaim conditions

Bug Fixes/Other
---------------
- Optimized a bunch of the entity targeters
- Fixed bugs with ConsumeHeldItem mechanic
- Fixed issues with look mechanic
- Fixed a lot of issues with the RandomSkill mechanic
- Fixed problems with Bees and Zombified Piglins w/ overrides
- Fixed extra spaces breaking inline skills in some cases
- Fixed shulkers with setColor mechanic
- Fixed doubles not working with setLevel mechanic
- Fixed NPE in Raytrace mechanic
- Fixed broken leftLeg and rightLeg aliases on animateArmorStand mechanic
- Fixed mmoitems drops in nested droptables not having the correct amount
- Fixed an NPE in commands
- Fixed some issues with location targeters
- Fixed an NPE in threat tables
- Fixed NPE with lost entities trying to unregister
- Fixed death messages not showing properly on PaperSpigot
- Fixed onShoot trigger for Ghasts
- Fixed weather mechanic not setting the weather to sunny/clear
- Fixed NPE with lost entities trying to unregister
- Fixed BonusLuckItem option in Droptables
- Fixed awkward issue with skeletons shooting a bow on some versions
- Fixed the fillChest mechanic
- Leather Horse Armor is now dyeable
- Fixed item Options.HideFlags not hiding all the flags
- Fixed an issue with TeleportIn mechanic attribute
- Fixed an issue with Threat mechanic
- Fixed bug with itemspray
- Fixed radiusY attribute for @BlocksInRadius
- Added placeholder support to velocity for Projectile mechanic
- Added placeholder support for Shield mechanic, Shoot mechanic, ShootShulker, mechanic
- Fixed an issue with Projectile mechanic when using these bullet types: ARROW, ITEM, and MYTHICITEM
- Fixed an issue with Summon mechanic not setting players as the parent
- Fixed an issue with HasInventorySpace condition
- Fixed a bug with nearestConditionalTarget ignoring players in 1.16.5
- Fixed an issue with ownerattacker and ownertarget not working as intended
- Fixed recursive mob loading issue
- RunAIGoal/TargetSelector will now parse premium AIs.
- Fixed an issue with NearestConditionalTarget ignoring players in 1.16.5
- Fixed blockwave and geyser leaving glitched blocks behind
- Fixed `ownerattacker` and `ownertarget` not working correctly in 1.16.5
- Fixed NPE in teleportto mechanic
- Fixed targeting issues with onAttack, onDamaged auras
- Fixed finite velocity error with projectiles
- Fixed Options.Interactable: false not working w/ ArmorStands closes 
- Fixed NPE in summon mechanic
- Fixed particleOrbital reversed=true option not working
- Fixed several ChunkUnload errors closes 
- Fixed some issues with non-paper spigot
- Fixed some targeting issues with auras

4.12.0
======

**Highlights**
----------
- New Skill Parameter system
- Disguise mechanic changes
- ChainMissile mecahnic
- Mob particles
- orElseCast condition action
- origin=@targeter option

General
-------

### Added Java 16 support

### Skill Parameters (Premium Feature)
Skill parameters are a new feature allowing you to more easily create generic skills and pass parameters to them from other skills. If that sounds confusing, here's an example!

Currently most people have a lot similar damage skills that are just tweaked a bit for all their different mobs for slight variances in damage, but they do basically the same thing otherwise.

**The old way of doing it:**
```
ShadowDamage20:
  Skills:
  - damage{amount=20}
  - some shadowy effect

ShadowDamage50:
  Skills:
  - damage{amount=50}
  - some shadowy effect

Mob1:
  Skills:
  - skill:ShadowDamage20 ~onAttack

Mob2:
  Skills:
  - skill:ShadowDamage50 ~onAttack
```

**With Skill Parameters, we can combine these all into a single skill! The new way:**
```
ShadowDamage:
  Skills:
  - damage{amount=<skill.damage>}

Mob1:
  Skills:
  - skill:ShadowDamage{damage=20} ~onAttack

Mob2:
  Skills:
  - skill:ShadowDamage{damage=50} ~onAttack
```
The "skill parameter" system will pass __any__ options from the **skill/metaskill** mechanic (except options that are specific to it) down the skill tree where you can reference them later. If a later skill passes the same parameter, it will overwrite it. These can be used anywhere placeholders are supported.

```
- skill{skill=SomeSkill;anything=2;somethingElse=5}

SomeSkill:
  Skills:
  - particles{amount=<skill.anything>}
  - damage{amount=<skill.somethingElse>}
```

Mobs
----
### NEW: EXPERIENCE_ORB
- Added EXPERIENCE_ORB mob type (why?)
- Can specify Options.Experience: amount

Mechanics
---------

### NEW: Origin Override (Premium Feature)
- Added `origin=@targeter` option to set the origin in any mechanic. Will pass through to any child mechanics.

### BreakBlock
- Added doDrops, doEffect, useTool options

### Disguise **MAJOR CHANGE** 
- Renamed disguise mechanic to disguiseOld
- Disguise now just accepts a LibsDisguises config string with d=

### FAWEPaste
- Added chestDropTable option
- Allows you to specify a MythicMobs droptable that will automagically populate and randomize any chests in that schematic when it's pasted

### FillChest
- Fills a chest at the targeted location with the contents of a droptable

### GiveItem
- Added fakeLooting=true option to play the pickup-item animation from the origin

### Messages
- Added audience option

### ModifyProjectile
- Added radius trait for orbitals

### Projectiles
- Greatly improved block collision detection
- Improved collision detection with huge mobs (giants, ghasts, etc)
- Improved collision detection with ModelEngine mobs

### RemoveAura
- You can now specify "ANY" to remove all auras from the target

### NEW: ChainMissile (Premium Feature)
- Combines the Chain and Missile mechanics, making a missile that will bounce between so many targets

### NEW: giveItemFromTarget
- Gives the caster an item while playing the pickup-item animation from the target entity or location

### NEW: raytraceTo (premium-only)
- Raytraces from the origin to the targeted location
- Same options as the raytrace mechanic

### NEW: ShootShulkerBullet
- Shoots a shulker bullet
- Has onTick, onHit, onEnd otpions

### NEW: clearThreat
- Clears the mob's threat table

### NEW: variableUnset{var=}

Effects
-------

### Audiences
- Added *caster* audience
- Added *@targeter* audience, allowing you to use any entity-targeter as an audience

### Particle Effects - Mob particles??? **(premium-only)**
- Added special type particle=mob on all particle effects
- You can then specify a MythicMob using mob=[type]
- This is a hacky way for you to use mobs as "particles" in effects using no-tick ArmorStands wearing models or using font characters. You can use things other than ArmorStands if you want, but we don't recommend it for performance.

### BlockWave
- Added velocityX, velocityY, velocityZ, and ignoreAir options

Targeters
---------
### NEW: @PlayerByName{name=""}
### NEW: @Vehicle

Conditions
----------
### New condition action: orElseCast
- If the condition isn't true, it will instead cast the given skill
```
SomeSkill:
  Conditions:
  - night orElseCast SomeOtherSkill
```

### NEW: isCaster
### NEW: isChild
### NEW: isLiving
### NEW: isMonster
### NEW: isPlayer
### NEW: isSprinting
- only works on players
### NEW: name{name=""}
- Matches a specific player name.
- Supports placeholders
### NEW: vehicleIsDead

Items
-----

### In-line item additions
- Added model, enchants, potioneffects, skullOwner and skullTexture to in-line item creation
```
diamond{display="test";enchants=DAMAGE_ALL:4,PROTECTION_ALL:4;model=2}
```

Placeholders
------------
- Added <caster.l.x.double>
- Added <caster.l.y.double>
- Added <caster.l.z.double>
- Added <skill.targets>

Compatibility
-------------
- Updated to latest LibsDisguises
- Removed CMI support completely
- Removed unused EffectLib compatibility

Bug Fixes/Other
---------------
- Name placeholder will now return the canonical mob type name if the mob has no display name set
- Fixed @ring targeter being slightly off-center
- Fixed audiences not working with certain particle effects
- Fixed invisible armorstands flickering for a tick when spawning
- Fixed an NPE in metaskills
- Fixed certain things such as bullets not showing up until after a reload
- Fixed NPE when spawning certain mobs on non-paper servers
- Fixed issues with mobs changing targets
- Fixed auras not finishing after the caster dies
- Fixed auras not falling off when a player dies
- Fixed bossbars not going away when spawner mobs despawn due to mm reload
- Fixed the setSpeed mechanic
- Fixed BreakBlock mechanic to respect worldguard with player casters
- Fixed an NPE in threat tables
- Fixed bug with auraRemove mechanic and removing specific aura stacks
- Fixed onShoot trigger to work with skeletons, withers, dragons, snowmen, ghasts, llamas, etc.
- Fixed item serialization issues when using old color codes and new hex colors making text italicized
- Fixed WorldTime condition
- Fixed NPE in item generation
- Fixed NPE in spawners
- Fixed BreakBlock mechanic not respecting regions/perms for players
- Fixed issues with hasAura condition
- Fixed some issues with and optimized @MobsInRadius targeter

Older Changelogs
================
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