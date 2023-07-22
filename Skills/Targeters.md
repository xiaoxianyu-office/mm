# Targeters

Targeters are used to determine what a skill targets when it is fired.

While targeters are technically optional (as the default targeter will usually be @trigger), forgetting a targeter is probably one of the most common mistakes people who are new to MythicMobs make.

When a targeter is used on the Skill mechanic, all of the skills inside of the meta-skill inherit the initial targeter. You can still overwrite the parent targeter for individual mechanics inside of the meta-skill by giving them their own targeter to use.

[[_TOC_]]

## Entity Targeters

### Single-Entity Targeters

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[Self][]                                                                                                                                                                            | @Caster<br>@Boss<br>@Mob                                                                                                                                                                            | Targets the caster of the mechanic                                                                                                                                                                            |
| @[Target][]                                                                                                                                                                            | @T                                                                                                                                                                            | Targets the caster's target                                                                                                                                                                            |
| @[Trigger][]                                                                                                                                                                            |    | Targets the entity that triggered the skill                                                                                                                                                                            |
| @[NearestPlayer][]                                                                                                                                                                            |    | Targets the nearest player in radius                                                                                                                                                                            |
| @[WolfOwner][]                                                                                                                                                                            |    | Targets the owner of the wolf                                                                                                                                                                            |
| @[Owner][]                                                                                                                          |    | Targets the [owner](/skills/mechanics/setowner) of the mob                                                                                                                          |
| @[Parent][]                                                                                                                          | @summoner                                                                                                                          | Targets the [parent](/skills/mechanics/setparent) of the mob                                                                                                                          |
| @[Mount][]                                                                                                                                                                            |                                                                                                                                                                            | Targets the entity that the mob is currently riding                                                                                                                                                                            |
| @[Children][]                                                                                                                          | @child<br>@summons                                                                                                                          | Targets any child entities summoned by the caster.                                                                                                                          |
| @[Father][]                                                                                                                          | @dad<br>@daddy                                                                                                                          | Targets the father of the casting mob.                                                                                                                          |
| @[Mother][]                                                                                                                          | @mom<br>@mommy                                                                                                                          | Targets the mother of the casting mob.                                                                                                                          |
| @[Passenger][]                                                                                                                          |    | Targets the rider of the casting mob.                                                                                                                          |
| @[PlayerByName][]                                                                                                                          | @specificplayer                                                                                                                          | Targets a specific player by name. Supports placeholders.                                                                                                                           |
| @[UniqueIdentifier][]                                                                                                                          | @UUID                                                                                                                          | Targets a specific entity by their UUID, supports placeholders                                                                                                                          |
| @[Vehicle][]                                                                                                                          |    | Targets the caster's vehicle                                                                                                                          |


### Multi-Entity Targeters

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[LivingInCone][]                                                                                                                                                                            | @entitiesInCone<br>@livingEntitiesInCone<br>@LEIC<br>@EIC                                                                                                                                                                            | Targets all living entities in cone with a specified angle, length and rotation relative to facing direction                                                                                                                                                                            |
| @[LivingInWorld][]                                                                                                                                                                            | @EIW                                                                                                                                                                            | Targets all living entities in the caster's world                                                                     |
| @[NotLivingNearOrigin][]                                                                                                                                                                            | @nonLivingNearOrigin<br>@NLNO                                                                                                                                                                            | Targets all non living entities in a radius near the origin                                                                     |
| @[PlayersInRadius][]                                                                                                                                                                            | @PIR                                                                                                                                                                            | Targets all players in the given radius                                                                                                                                                                            |
| @[MobsInRadius][]                                                                                                                                                                            | @MIR                                                                                                                                                                            | Targets all mythicmobs or vanilla overrides of the given type in a radius                                                                   |
| @[EntitiesInRadius][]                                                                                                                                   | @livingEntitiesInRadius<br>@livingInRadius<br>@allInRadius<br>@EIR                                                                                                                          | Targets all entities in the given radius.                                                                                                                                   |
| @[EntitiesInRing][]                                                                                                                                   | @EIRR                                                                                                                          | Targets all entities in the given ring.                                                                                                                                   |
| @[PlayersInWorld][]                                                                                                                                   | @World                                                                                                                                   | Targets all players in the current world.                                                                        |
| @[PlayersOnServer][]                                                                                                                                   | @Server<br>@Everyone                                                                                                                                   | Targets all players in the server.                                                                                                                                   |
| @[PlayersInRing][]                                                                                                                                   |    | Target all players between the specified min and max radius.                                                                                                                                   |
| @[PlayersNearOrigin][]                                                                                                                                   |    | Targets players near the [origin](/skills/targeters/origin) of a meta-skill.                                                                                                                                   |
| @[MobsNearOrigin][]                                                                                                                                   |    | Targets all MythicMobs or vanilla overrides of the given type(s) in a radius around the origin                                                                                                                                   |
| @[EntitiesNearOrigin][]                                                                                                                                                                            | @ENO                                                                                                                                                                            | Targets all entities near the [origin](/skills/targeters/origin) of a meta-skill                                                                                                                                                                            |
| @[Siblings][]                                                                                                                                                                            | @sibling<br>@brothers<br>@sisters                                                                                                                                                                            | Targets any mobs that share the same parent as the caster.                                                                                                                                                                            |
| @[ItemsNearOrigin][]                                                                                                                                                                            |    | Targets item drops near the [origin](/skills/targeters/origin) of a meta-skill.                                                                                                                                                                            |
| @[ItemsInRadius][]                                                                                                                                                                            | @IIR                                                                                                                                                                            | Targets all item drops in the given radius                                                                       |


### ThreatTable Targeters

These targeters only work if the mob has [Threat Tables](/Mobs/ThreatTables) enabled.

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[ThreatTable][]                                                                                                                          | @TT                                                                                                                          | Targets every entity on the casting mob's threat table                                                                                                                         |
| @[ThreatTablePlayers][]                                                                                                                          |    | Targets all the players on the casting mob's threat table                                                                                                                          |
| @[RandomThreatTarget][]                                                                                                                          | @RTT                                                                                                                          | Targets a random entity on the casting mob's threat table                                                                                                                          |
| @[RandomThreatTargetLocation][]                                                                                                                          | @RTTL                                                                                                                          | Targets the location of a random entity on the casting mob's threat table                                                                                                                          |



## Location Targeters

### Single-Location Targeters

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[SelfLocation][]                                                                                                                          | @casterLocation<br>@bossLocation<br>@mobLocation                                                                                                                          | Targets the caster's location                                                                                                                          |
| @[SelfEyeLocation][]                                                                                                                          | @eyeDirection<br>@casterEyeLocation<br>@bossEyeLocation<br>@mobEyeLocation                                                                                                                          | Targets the caster's eye location                                                                                                                          |
| @[Forward][]                                                                                                                          |   | Targets a location in front of caster's facing direction                                                                                                                          |
| @[ProjectileForward][]                                                                                                                          |    | Targets a location in front of the casting projectile, relative to its direction                                                                                                                          |
| @[TargetLocation][]                                                                                                                          | @targetloc<br>@TL | Targets the caster's target's location                                                                                                                                                                                                                |
| @[TriggerLocation][]                                                                                                                                                                            |    | Targets the location of the entity that triggered the skill                                                                                                                                                                            |
| @[SpawnLocation][]                                                                                                                          |    | Targets the world's spawn location.                                                                                                                          |
| @[CasterSpawnLocation][]                                                                                                                          |    | Targets the location the caster spawned at.                                                                                                                          |
| @[Location][]                                                                                                                          |    | Targets the specified coordinates in the caster's world.                                                                                                                          |
| @[Origin][]                                                                                                                          | @source                                                                                                                          | Targets the location of the "origin" or "source" of a meta-skill. While that is usually the casting mob, there are special cases where this is not true (such as with the Projectile Skill, where the "origin" is the location of the projectile).                                                                                                                          |
| @[ObstructingBlock][]                                                                                                                          |    | Tries to target the block in front of the caster that is obstructing it                                                                                                                          |
| @[TrackedLocation][]                                                                                                                          |    | Targets the mob's tracked location                                                                                                                          |
| @[NearestStructure][]                                                                                                                          |    | Targets the nearest structure of the specified type within a radius in the caster's world                                                                                                                          |
| @[VariableLocation][]                                                                                                                          | @varLocation                                                                                                                          | Targets the location stored in the specified variable                                                                                                                          |


### Multi-Location Targeters

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[ForwardWall][]                                                                                                                          |    | Targets a plane in front of the caster                                                                                                                          |
| @[PlayerLocationsInRadius][]                                                                                                                          | @PLIR                                                                                                                          | Targets all player locations in the given radius                                                                                    |
| @[Ring][]                                                                                                                          |    | Target points to form a ring of locations                                                                                                                          |
| @[Cone][]                                                                                                                                                                            |    | Returns the # of points target locations that comprise a cone (Note: Cone is fixed on the y-axis, and cannot be rotated up or down)                                                                                                                          |
| @[Sphere][]                                                                                                                                                                            |    | Targets points in a sphere around the caster                                                                                                                                                                            |
| @[Rectangle][]                                                                                                                                                                            | @cube<br>@cuboid                                                                                                                                                                            | Returns the # of points target locations that comprise a rectangle                                                                                                                                                                            |
| @[RandomLocationsNearCaster][]                                                                                                                                                                            | @RLO<br>@randomLocationsOrigin<br>@RLNO                                                                                                                                                                            | Targets random locations near the origin of a skill.                                                                                                                                                                            |
| @[RandomLocationsNearOrigin][]                                                                                                                                                                            | @RLO<br>@randomLocationsOrigin<br>@RLNO                                                                                                                                                                            | Targets random locations near the origin of a skill.                                                                                                                                                                            |
| @[RingAroundOrigin][]                                                                                                                                                                            | @ringOrigin<br>@RAO                                                                                                                                                                            | Targets locations in a specified ring around the origin.                                                                                                                                                                            |
| @[Spawners][]                                                                                                                          |    | Targets the location of the specified spawners.                                                                                                                          |



## Meta Targeters

The targeters below are called "meta-targeters" (or "special targeters"). They target relative to an [inherited target](Metaskills#inheritance). For example:
```yaml
# Mob file
Laser:
  Type: CREEPER
  Display: 'Laser'
  Health: 12
  AITargetSelectors:
  - 0 clear
  - 1 players
  Skills:
  - skill{s=Laser} @target
```
```yaml
# Skill file
Laser:
  Skills:
  - ignite @EntitiesInLine{r=1}
```
In the example skill above, the "ignite" mechanic will target entities between the caster and the targeter specified in `- skill{s=Laser} @target`, i.e. a line between the caster and the caster's target.

Some meta-targeters also allow the mechanic to be casted "fromOrigin". This will change the starting location of the meta-targeter to be @Origin rather than the caster, which can allow for some complex effects, particularly when used with Projectiles.


### Meta-Entity Targeters

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[LivingInLine][]                                                                                                                          | @entitiesInLine<br>@livingEntitiesInLine<br>@LEIL<br>@EIL                                                                                                                          | Targets any entities in a line between the inherited target and the casting mob.                                                                                                                          |
| @[LivingNearTargetLocation][]                                                                                                                          | @LNTL<br>@ENTL<br>@ENT                                                                                                                          | Targets all living entities near the inherited target.                                                                                                                                                        |
| @[PlayersNearTargetLocations][]                                                                                                                          | @playersNearTargetLocation<br>@PNTL                                                                                                                          | Targets all players near the inherited targets.                                                                                                                          |
| @[TargetedTarget][]                                                                                                                          | @Targeted                                                                                                                          | Targets the inherited targeted entities.                                                                                                                          |


### Meta-Location Targeters

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[Line][]                                                                                                                          |    | Targets locations between the mob and the inherited targets.                                                                                                                                                     |
| @[RandomLocationsNearTargets][]                                                                                                                          | @randomLocationsNearTarget<br>@randomLocationsNearTargetEntities<br>@randomLocationsNearTargetLocations<br>@RLNT<br>@RLNTE<br>@RLNTL                                                                                                                          | Targets random locations around the inherited targets.                                                                                                                          |
| @[FloorOfTargets][]                                                                                                                          | @FOT<br>@floorsOfTarget                                                                                                                          | Targets the blocks underneath the inherited targets.                                                                                                                                                            |
| @[LocationsOfTargets][]                                                                                                                          | @locationOfTarget<br>@LOT                                                                                                                          | Targets the location of the inherited target entities.                                                                                                                                                                   |
| @[TargetedLocation][]                                                                                                                          | @targetedLocations<br>@targetedLoc                                                                                                                          | Targets the location of the inherited target locations.                                                                                            |
| @[BlocksInRadius][]                                                                                                                          | @BIR                                                                                                                          | Targets all blocks in a radius of the inherited targets.                                                                                                                          |
| @[TargetBlock][]                                                                                                                          |    | Targets the block the casting player is looking at.                                                                                                                          |
| @[BlocksInChunk][]                                                                                                                          | @BIC                                                                                                                          | Targets all blocks in a chunk relative to the inherited target.                                            |
| @[BlocksNearOrigin][]                                                                                                                          | @BNO                                                                                                                          | Targets all blocks in a radius around the origin of the metaskill.                                                                                                                                                     |
| @[BlockVein][]                                                                                                                          | @vein<br>@bv                                                                                                                          | Target all adjancent blocks that match the blocktype, starting from the origin of the skill.                                                                                                                                                     |


### None Targeter

| Targeter | Shorthand | Description                                                      |
|----------|-----------|------------------------------------------------------------------|
| @None    |           | Provides no target. (Useful for mechanics with no target input.) |



# Common Attributes
There are some common attributes that can be used in most of the Targeters, depending on the targeter's returned value

## All Targeters

### Sudo Attributes
| Attribute                                | Shorthand        | Description                                                                                                      |
| ---------------------------------------- | ---------------- | ----------------------------------------- |
| sudoparent                               | fromparent, ofparent, asparent, parent, ofparent                      | If this attribute is set to `true`, the targeter will be parsed as if it was the [Parent][] of the casting entity executing the mechanic|
| sudoowner                                | fromowner, ofowner, asowner, owner, ofowner                      | If this attribute is set to `true`, the targeter will be parsed as if it was the [Owner][] of the casting entity executing the mechanic |
| sudotrigger                                | fromtrigger, oftrigger, astrigger, trigger, oftrigger                      | If this attribute is set to `true`, the targeter will be parsed as if it was the [Trigger][] of the skilltree executing the mechanic |

In this example, [the mob will keep getting teleported in front of its owner](https://cdn.discordapp.com/attachments/523443579574681600/1101186712174088253/a.gif), since the `Forward` targeter is using the `sudoowner` attribute, and is, as such, getting parsed as if it was the owner of the casting mob executing the mechanic
```yaml
TestOwner:
  Type: Wolf
  Skills:
  - setOwner @NearestPlayer{r=99} ~onSpawn
  - tp @Forward{f=5;y=1;sudoowner=true} ~onTimer:1
```


## Location Targeters
| Attribute                                | Shorthand        | Description                                                                                                      |
| ---------------------------------------- | ---------------- | ----------------------------------------- |
| xoffset                                  | xo, x            | Centers the offset on the x axis           |
| yoffset                                  | yo, y            | Centers the offset on the y axis           |
| zoffset                                  | zo, z            | Centers the offset on the z axis           |
| forwardOffset                            | foffset, fo      | Centers forward and backward offset, based on the caster's viewing angle |
| sideOffset                               | soffset, so      | Centers left and right offset, based on the caster's viewing angle |
| rotatex                                  | rotx             | Rotation on the x axis                    |
| rotatey                                  | roty             | Rotation on the y axis                    |
| rotatez                                  | rotz             | Rotation on the z axis                    |
| coordinatex                              | cx               | Sets the x axis coordinate                    |
| coordinatey                              | cy               | Sets the y axis coordinate                    |
| coordinatez                              | cz               | Sets the z axis coordinate                    |
| blocktypes                               | blocktype, bt   | Only targets selected block types. Multiple blocks can be listed by separating them using a `,`<br>You can add a `#` at the front of the type to indicate that the block only needs to match part of the type, add `@` to indicate that the block only needs to match the start of the type |
| blockignores                             | blockignore      | Excludes selected block types from the targeter. Multiple blocks can be listed by separating them using a `,` |
| coordinateyaw                            | cyaw             | Sets the yaw value                        |
| coordinatepitch                          | cpitch           | Sets the pitch value                        |
| blockcentered                            | centered         | Boolean value. If set to true, the center of the block at the target location will be targeted, instead of the target location itself |


# Targeter Options

## Target Filters

Target Filters allow you to filter out certain targets, and makes targeters a lot more flexible.

They are used with two options (available on ANY entity-targeter):

-   ignore=X
-   target=X

For example, to make a targeter that will ignore any players or non-hostile mobs, you'd use this:

    damage{a=20} @EntitiesInRadius{r=10;ignore=players,animals}

To make a targeter ONLY target players, you'd do something like this:

    skill{s=ASkill} @EntitiesInRadius{r=5;target=players}

Possible filters include:

-   self
-   animals *(non-hostile mobs)*
-   armorstands/armor_stands
-   creative *(ignored by default)*
-   creatures *(any type of sentient entity)*
-   flyingmobs
-   marker
-   monsters *(hostile mobs)*
-   NPCs *(Citizens NPCs, ignored by default)*
-   players
-   samefaction *(mobs marked with the same faction type)*
-   spectators *(ignored by default)*
-   vanilla
-   villager
-   watermobs
-   owner
-   More coming later...

You can also turn off specific filters by just adding the option
**targetXXXXX** replacing XXXXX with the filter name, e.g.
**targetPlayers=false** or **targetcreative=true**

Note: As of MM 4.15 or MM 5.0, you can set the default target filters in MythicMobs/config.yml

## Target Limits

All entity and location targeters also support target limits (as of v5.0.4). With this you can limit how many entities/locations are targeted, including the order in which they are selected.

This is done with the options:

-   limit=#
-   sort=X

Lets say you want your ability to only target the 2 nearest players within 30 blocks. To do this, you'd simply set the limit 2 to and sort by nearest:

-   **@PlayersInRadius{r=30;limit=2;sort=NEAREST}**

Currently, sort can have the following values:

**General sorters:**
- NONE *(usually sorts by how long the entity has existed)*
- RANDOM
- NEAREST
- FURTHEST

**Entity Only Sorters**
- HIGHEST_HEALTH
- LOWEST_HEALTH
- HIGHEST_THREAT
- LOWEST_THREAT


<!-- LINKS -->
<!-- Single Entity Targeters -->
  [Children]: /Skills/Targeters/Children
  [Father]: /Skills/Targeters/Father
  [Mother]: /Skills/Targeters/Mother
  [Mount]: /Skills/Targeters/Mount
  [NearestPlayer]: /Skills/Targeters/NearestPlayer
  [Owner]: /Skills/Targeters/Owner
  [Parent]: /Skills/Targeters/Parent
  [Passenger]: /Skills/Targeters/Passenger
  [PlayerByName]: /Skills/Targeters/PlayerByName
  [Self]: /Skills/Targeters/Self
  [Target]: /Skills/Targeters/Target
  [Trigger]: /Skills/Targeters/Trigger
  [UniqueIdentifier]: /Skills/Targeters/UniqueIdentifier
  [Vehicle]: /Skills/Targeters/Vehicle
  [WolfOwner]: /Skills/Targeters/WolfOwner
<!-- Multi Entity Targeters -->
  [EntitiesInRadius]: /Skills/Targeters/EntitiesInRadius
  [EntitiesInRing]: /Skills/Targeters/EntitiesInRing
  [EntitiesNearOrigin]: /Skills/Targeters/EntitiesNearOrigin
  [ItemsInRadius]: /Skills/Targeters/ItemsInRadius
  [ItemsNearOrigin]: /Skills/Targeters/ItemsNearOrigin
  [LivingInCone]: /Skills/Targeters/LivingInCone
  [LivingInWorld]: /Skills/Targeters/LivingInWorld
  [MobsInRadius]: /Skills/Targeters/MobsInRadius
  [MobsNearOrigin]: /Skills/Targeters/MobsNearOrigin
  [NotLivingNearOrigin]: /Skills/Targeters/NotLivingNearOrigin
  [PlayerLocationsInRadius]: /Skills/Targeters/PlayerLocationsInRadius
  [PlayersInRadius]: /Skills/Targeters/PlayersInRadius
  [PlayersInRing]: /Skills/Targeters/PlayersInRing
  [PlayersInWorld]: /Skills/Targeters/PlayersInWorld
  [PlayersNearOrigin]: /Skills/Targeters/PlayersNearOrigin
  [PlayersOnServer]: /Skills/Targeters/PlayersOnServer
  [Siblings]: /Skills/Targeters/Siblings
<!-- ThreatTable Targeters -->
  [ThreatTable]: /Skills/Targeters/ThreatTable
  [ThreatTablePlayers]: /Skills/Targeters/ThreatTablePlayers
  [RandomThreatTarget]: /Skills/Targeters/RandomThreatTarget
  [RandomThreatTargetLocation]: /Skills/Targeters/RandomThreatTargetLocation
<!-- Single Location Targeters -->
  [CasterSpawnLocation]: /Skills/Targeters/CasterSpawnLocation
  [Forward]: /Skills/Targeters/Forward
  [Location]: /Skills/Targeters/Location
  [NearestStructure]: /Skills/Targeters/NearestStructure
  [ObstructingBlock]: /Skills/Targeters/ObstructingBlock
  [Origin]: /Skills/Targeters/Origin
  [ProjectileForward]: /Skills/Targeters/ProjectileForward
  [SelfEyeLocation]: /Skills/Targeters/SelfEyeLocation
  [SelfLocation]: /Skills/Targeters/SelfLocation
  [SpawnLocation]: /Skills/Targeters/SpawnLocation
  [VariableLocation]: /Skills/Targeters/VariableLocation
  [TargetBlock]: /Skills/Targeters/TargetBlock
  [TargetLocation]: /Skills/Targeters/TargetLocation
  [TrackedLocation]: /Skills/Targeters/TrackedLocation
  [TriggerLocation]: /Skills/Targeters/TriggerLocation
<!-- Multi Location Targeters -->
  [Cone]: /Skills/Targeters/Cone
  [ForwardWall]: /Skills/Targeters/ForwardWall
  [RandomLocationsNearOrigin]: /Skills/Targeters/RandomLocationsNearOrigin
  [RandomLocationsNearCaster]: /Skills/Targeters/RandomLocationsNearCaster
  [Rectangle]: /Skills/Targeters/Rectangle
  [RingAroundOrigin]: /Skills/Targeters/RingAroundOrigin
  [Ring]: /Skills/Targeters/Ring
  [Spawners]: /Skills/Targeters/Spawners
  [Sphere]: /Skills/Targeters/Sphere
<!-- Meta Targeters -->
  [BlocksInRadius]: /Skills/Targeters/BlocksInRadius
  [BlocksInChunk]: /Skills/Targeters/BlocksInChunk
  [BlocksNearOrigin]: /Skills/Targeters/BlocksNearOrigin
  [BlockVein]: /Skills/Targeters/BlockVein
  [FloorOfTargets]: /Skills/Targeters/FloorOfTargets
  [Line]: /Skills/Targeters/Line
  [LivingInLine]: /Skills/Targeters/LivingInLine
  [LivingNearTargetLocation]: /Skills/Targeters/LivingNearTargetLocation
  [LocationsOfTargets]: /Skills/Targeters/LocationsOfTargets
  [PlayersNearTargetLocations]: /Skills/Targeters/PlayersNearTargetLocations
  [RandomLocationsNearTargets]: /Skills/Targeters/RandomLocationsNearTargets
  [TargetedLocation]: /Skills/Targeters/TargetedLocation
  [TargetedTarget]: /Skills/Targeters/TargetedTarget