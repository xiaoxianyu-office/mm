Targeters are used to determine what a skill targets when it is fired.

While targeters are technically optional (as the default targeter will usually be @trigger), forgetting a targeter is probably one of the most common mistakes people who are new to MythicMobs make.

When a targeter is used on the Skill mechanic, all of the skills inside of the meta-skill inherit the initial targeter. You can still overwrite the parent targeter for individual mechanics inside of the meta-skill by giving them their own targeter to use.

If entity targets are passed to a location-based mechanic, it will use the entity's location.

[[_TOC_]]

# Additional Targeters
Links to targeters added by addon plugins. Any targeters from these links will not work without that plugin installed.

- [ModelEngine 4](https://git.mythiccraft.io/mythiccraft/model-engine-4/-/wikis/Skills/Targeters)
- [Mythic Crucible](https://git.mythiccraft.io/mythiccraft/mythiccrucible/-/wikis/Skills/Targeters)
- [Mythic Enchantments](https://git.mythiccraft.io/mythiccraft/mythicenchants/-/wikis/Skills/Targeters)
- [MCPets](https://mcpets.gitbook.io/mcpets/tutorials/mythicmobs-features#targeters)

# Targeters

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
| @[Mount][]                                                                                                                                                                            |                                                                                                                                                                            | Targets the caster's original [mount](/Mobs/Mobs#mount)                                                                                                                                                                            |
| @[Father][]                                                                                                                          | @dad<br>@daddy                                                                                                                          | Targets the father of the casting mob.                                                                                                                          |
| @[Mother][]                                                                                                                          | @mom<br>@mommy                                                                                                                          | Targets the mother of the casting mob.                                                                                                                          |
| @[Passenger][]                                                                                                                          |    | Targets the rider of the casting mob.                                                                                                                          |
| @[PlayerByName][]                                                                                                                          | @specificplayer                                                                                                                          | Targets a specific player by name. Supports placeholders.                                                                                                                           |
| @[UniqueIdentifier][]                                                                                                                          | @UUID                                                                                                                          | Targets a specific entity by their UUID, supports placeholders                                                                                                                          |
| @[Vehicle][]                                                                                                                          |    | Targets the caster's vehicle                                                                                                                          |
| @[InteractionLastAttacker][]                                                                                                                          | @lastAttacker                                                                                                                          | Targets the last entity that attacked the casting `INTERACTION` entity                                                                                                                         |
| @[InteractionLastInteract][]                                                                                                                          | @lastInteract                                                                                                                          | Targets the last entity that interacted with the casting `INTERACTION` entity                                                                                                                         |
| @[OwnerLocation][]                                                                                                                          |    | Targets the position of the owner of the mob                                                                                                                         |
| @[ParentLocation][]                                                                                                                          | @summonerlocation                                                                                                                          | Targets the position of the parent of the mob                                                                                                                         |


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
| @[EntitiesInRingNearOrigin][]                                                                                                                                   | @ERNO                                                                                                                          | Targets all entities in the given ring around the origin.                                                                                                                                   |
| @[PlayersInWorld][]                                                                                                                                   | @World                                                                                                                                   | Targets all players in the current world.                                                                        |
| @[PlayersOnServer][]                                                                                                                                   | @Server<br>@Everyone                                                                                                                                   | Targets all players in the server.                                                                                                                                   |
| @[PlayersInRing][]                                                                                                                                   |    | Target all players between the specified min and max radius.                                                                                                                                   |
| @[PlayersNearOrigin][]                                                                                                                                   | @PNO                                                                                                                          | Targets players near the [origin](/skills/targeters/origin) of a meta-skill.                                                                                                                                   |
| @[TrackedPlayers][]                                                                                                                                                                            | @tracked                                                                                                | Targets players that are within the render distance of the caster                                                                       |
| @[MobsNearOrigin][]                                                                                                                                   |    | Targets all MythicMobs or vanilla overrides of the given type(s) in a radius around the origin                                                                                                                                   |
| @[EntitiesNearOrigin][]                                                                                                                                                                            | @ENO                                                                                                                                                                            | Targets all entities near the [origin](/skills/targeters/origin) of a meta-skill                                                                                                                                                                            |
| @[Children][]                                                                                                                          | @child<br>@summons                                                                                                                          | Targets any child entities summoned by the caster.                                                                                                                          |
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
| @[TargetPredictedLocation][]                                                                                                                          | @targetPredictedLoc<br>@TPL<br>@PredictedTargetLocation | Targets the predicted location at which the caster's top target will be after an amount of ticks has elapsed, based on its current movement speed                                                                                                                                                                                                                |
| @[TriggerLocation][]                                                                                                                                                                            |    | Targets the location of the entity that triggered the skill                                                                                                                                                                            |
| @[SpawnLocation][]                                                                                                                          |    | Targets the world's spawn location.                                                                                                                          |
| @[CasterSpawnLocation][]                                                                                                                          |    | Targets the location the caster spawned at.                                                                                                                          |
| @[Location][]                                                                                                                          |    | Targets the specified coordinates in the caster's world.                                                                                                                          |
| @[Origin][]                                                                                                                          | @source                                                                                                                          | Targets the location of the "origin" or "source" of a meta-skill. While that is usually the casting mob, there are special cases where this is not true (such as with the Projectile Skill, where the "origin" is the location of the projectile).                                                                                                                          |
| @[ObstructingBlock][]                                                                                                                          |    | Tries to target the block in front of the caster that is obstructing it                                                                                                                          |
| @[TargetBlock][]                                                                                                                          |    | Targets the block the casting player is looking at.                                                                                                                          |
| @[TrackedLocation][]                                                                                                                          |    | Targets the mob's tracked location                                                                                                                          |
| @[NearestStructure][]                                                                                                                          |    | Targets the nearest structure of the specified type within a radius in the caster's world                                                                                                                          |
| @[VariableLocation][]                                                                                                                          | @varLocation                                                                                                                          | Targets the location stored in the specified variable                                                                                                                          |
| @[HighestBlock][]                                                                                                                          |    | Targets the highest block at the skill origin                                                      |
| @[PlayerLocationByName][]                                                                                                                          |    | Targets a specific player's location by their name                                                      |
| @[EscapeLocation][]                                                                                                                          |    | Targets a nearby safe escape location like how an Enderman would choose its teleport destination                                                      |


### Multi-Location Targeters

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[ForwardWall][]                                                                                                                          |    | Targets a plane in front of the caster                                                                                                                          |
| @[PlayerLocationsInRadius][]                                                                                                                          | @PLIR                                                                                                                          | Targets all player locations in the given radius                                                                                    |
| @[Pin][]                                                                                                                          |    | Targets the location(s) of a [pin](/Pins).                                                                                                                          |
| @[Ring][]                                                                                                                          |    | Target points to form a ring of locations                                                                                                                          |
| @[RandomRingPoint][]                                                                                                                          |    | Targets random points in a ring around the caster                                                                                                                          |
| @[Cone][]                                                                                                                                                                            |    | Returns the # of points target locations that comprise a cone (Note: Cone is fixed on the y-axis, and cannot be rotated up or down)                                                                                                                          |
| @[Sphere][]                                                                                                                                                                            |    | Targets points in a sphere around the caster                                                                                                                                                                            |
| @[Rectangle][]                                                                                                                                                                            | @cube<br>@cuboid                                                                                                                                                                            | Returns the # of points target locations that comprise a rectangle                                                                                                                                                                            |
| @[RandomLocationsNearCaster][]                                                                                                                                                                            | @randomLocations<br>@RLNC                                                                                                                                                                            | Targets random locations near the caster.                                                                                                                                                                            |
| @[RandomLocationsNearOrigin][]                                                                                                                                                                            | @RLO<br>@randomLocationsOrigin<br>@RLNO                                                                                                                                                                            | Targets random locations near the origin of a skill.                                                                                                                                                                            |
| @[BlocksNearOrigin][]                                                                                                                          | @BNO                                                                                                                          | Targets all blocks in a radius around the origin of the metaskill.                                                                                                                                                     |
| @[RingAroundOrigin][]                                                                                                                                                                            | @ringOrigin<br>@RAO                                                                                                                                                                            | Targets locations in a specified ring around the origin.                                                                                                                                                                            |
| @[Spawners][]                                                                                                                          |    | Targets the location of the specified spawners.                                                                                                                          |
| @[BlocksInPinRegion][]                                                                                                                                                                            |    | Targets the blocks in a region delimited by two pins                                                                                                                                                                            |
| @[ChunksInWERegion][]                                                                                                                          | @chunksInWGRegion                                                                                       | Targets the 0,0 chunk corners of the chunks in a specified WorldGuard region                                                                                                                          |



## Meta Targeters

Meta Targeters targets relative to an [inherited target](/Skills/Metaskills#inheritance). For example:
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

Some meta targeters also allow the mechanic to be casted "fromOrigin". This will change the starting location of the meta-targeter to be @Origin rather than the caster, which can allow for some complex effects, particularly when used with Projectiles.


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
| @[BlocksInChunk][]                                                                                                                          | @BIC                                                                                                                          | Targets all blocks in a chunk relative to the inherited target.                                            |
| @[BlockVein][]                                                                                                                          | @vein<br>@bv                                                                                                                          | Target all adjancent blocks that match the blocktype, starting from the origin of the skill.                                                                                                                                                     |


## Special Targeters

| Targeter | Shorthand | Description                                                                     |
|----------|-----------|---------------------------------------------------------------------------------|
| @[None]  |           | Provides no target. (Useful for mechanics with no target input.)                |
| @[Region]|           | Special targeter to target a region. Only works with specific mechanics         |


# Common Attributes
There are some common attributes that can be used in most of the Targeters, depending on the targeter's returned value

## All Targeters

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| targetconditions                         | conditions, cond, c | [Inline Target Conditions](/Skills/Inline-Conditions#targetconditions) |<!--type:Conditions-->|
| fallback  | fb        | The fallback targeter to use, if this one returns no target          |<!--type:Targeter-->|

### Sudo Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| sudoparent                               | fromparent, ofparent, asparent, parent, ofparent                      | If this attribute is set to `true`, the targeter will be parsed as if it was the [Parent][] of the casting entity executing the mechanic | |
| sudoowner                                | fromowner, ofowner, asowner, owner, ofowner                      | If this attribute is set to `true`, the targeter will be parsed as if it was the [Owner][] of the casting entity executing the mechanic | |
| sudotrigger                                | fromtrigger, oftrigger, astrigger, trigger, oftrigger                      | If this attribute is set to `true`, the targeter will be parsed as if it was the [Trigger][] of the skilltree executing the mechanic | |

In this example, [the mob will keep getting teleported in front of its owner](https://cdn.discordapp.com/attachments/523443579574681600/1101186712174088253/a.gif), since the `Forward` targeter is using the `sudoowner` attribute, and is, as such, getting parsed as if it was the owner of the casting mob executing the mechanic
```yaml
TestOwner:
  Type: Wolf
  Skills:
  - setOwner @NearestPlayer{r=99} ~onSpawn
  - tp @Forward{f=5;y=1;sudoowner=true} ~onTimer:1
```

## Common Entity Targeters Attributes
| Attribute <!-- ETA --> | Aliases   | Description                                             | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| useboundingbox                           | bb               | If the targeter is performing a distance check, this option allows it to check against the bounding box of the target instead of the center of its hitbox | |
| unique                                   | u                | The maximum number of times an entity can be targeted. Defaults to 1, disable with 0. This is mostly used for meg models with multiple hitboxes | |
| nomegbb                                  | nmb              | Whether MEG sub hitboxes should be filtered out | |

## Common Location Targeters Attributes
| Attribute <!-- LTA -->| Aliases   | Description                                              | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| xoffset                                  | xo, x            | Centers the offset on the x axis           | |
| yoffset                                  | yo, y            | Centers the offset on the y axis           | |
| zoffset                                  | zo, z            | Centers the offset on the z axis           | |
| forwardOffset                            | foffset, fo      | Centers forward and backward offset, based on the caster's viewing angle | 0 |
| sideOffset                               | soffset, so      | Centers left and right offset, based on the caster's viewing angle | 0 |
|  upoffset                                | uoffset, uo      | Centers up and down offset, based on the caster's viewing angle | 0 |
| rotatex                                  | rotx             | Rotation on the x axis                    | |
| rotatey                                  | roty             | Rotation on the y axis                    | |
| rotatez                                  | rotz             | Rotation on the z axis                    | |
| coordinatex                              | cx               | Sets the x axis coordinate                    | |
| coordinatey                              | cy               | Sets the y axis coordinate                    | |
| coordinatez                              | cz               | Sets the z axis coordinate                    | |
| length                                   |                  | Multiplied the direction vector by the specified value                            | |
| blocktypes                               | blocktype, bt    | Only targets selected block types. Multiple blocks can be listed by separating them using a `,`<br>You can add a `#` at the front of the type to indicate that the block only needs to match part of the type, add `@` to indicate that the block only needs to match the start of the type<br>You can add a `*` at the front of the type to indicate that the one specified is not a block type, but a [block tag](https://minecraft.wiki/w/Tag#Block_tags_2) (example: `blocktype=*sculk_replaceable`  ) | |
| blockignores                             | blockignore, bi  | Excludes selected block types from the targeter. Multiple blocks can be listed by separating them using a `,`<br>Can use the special syntaxes specified in `blocktype` | |
| coordinateyaw                            | cyaw             | Sets the yaw value                        | |
| coordinatepitch                          | cpitch           | Sets the pitch value                        | |
| blockcentered                            | centered         | Boolean value. If set to true, the center of the block at the target location will be targeted, instead of the target location itself | |
| faulty    |           | Whether the mechanic should use the old vector formula        | false |
| blockSurface | surface | Whether the plugin should attempt to adjust the location to be on a surface | false |
| blockSurfaceTolerance | surfaceTolerance | The tolerance used when searching for a surface, when `blockSurface` is set to `true`| 5 |


# Targeter Options

## Target Filters

Target Filters allow you to filter out certain targets, and makes targeters a lot more flexible.

They are used with two attributes (available on ANY entity-targeter):

| Attribute <!-- ETA --> | Aliases   | Description                                             | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| target    |           | The entity types to target                                           |         |
| ignore    |           | The entity types to not target                                       |         |


For example, to make a targeter that will ignore any players or non-hostile mobs, you'd use this:

```yaml
  - damage{a=20} @EntitiesInRadius{r=10;ignore=players,animals}
```
To make a targeter ONLY target players, you'd do something like this:

```yaml
  - skill{s=ASkill} @EntitiesInRadius{r=5;target=players}
```

> You can set the default target filters in MythicMobs/config/config-skills.yml


Possible filters include:

#### Target Attribute
| Target Filter| Aliases| Description                                                                   |
|-----------|-----------|--------------------------------------------------------------------------------|
| ground    |         | Whether to target ground entities. Will ignore flying and water entities if used |
| water     |         | Whether to target water entities. Will ignore flying and ground entities if used |
| flying    |         | Whether to target flying entities. Will ignore ground and water entities if used |
| self      | caster    | Whether the caster of the mechanic can be targetd                              |
| player    |           | Whether players can be targeted                                                |
| creative  |           | Whether creative mode players can be targeted                                  |
| spectator |           | Whether spectator mode players can be targeted                                 |
| armorstand| armor_stand | Whether armor stands can be targeted                                         |
| marker    |           | Whether markers can be targeted                                                |
| npc       |           | Whether Citizens NPCs can be targeted                                          |
| animal    |           | Whether animals can be targeted                                                |
| creature  |           | Whether creatures can be targeted                                              |
| monster   |           | Whether monsters can be targeted                                               |
| villager  |           | Whether villagers can be targeted                                              |

> If neither `ground`, `water` and `flying` are used and the default filters do not include any of them, then `Players`, `ArmorStands`, `Markers`, `Creative`, `Spectator`, `CitizensNPCs`, `Animals`, `Creatures`, `Monsters` and `Villagers` will also be ignored

#### Ignore Attribute
| Ignore Filter | Aliases   | Description                                                                |
|-----------|-----------|--------------------------------------------------------------------------------|
| player    |           | Whether players shouldn't be targetd                                           |
| creative  |           | Whether creative mode players shouldn't be targeted                            |
| spectator |           | Whether spectator mode players shouldn't be targeted                           |
| armorstand| armor_stand | Whether armor stands shouldn't be targeted                                   |
| marker    |           | Whether markers shouldn't be targeted                                          |
| npc       |           | Whether Citizens NPCs shouldn't be targeted                                    |
| animal    |           | Whether animals shouldn't be targeted                                          |
| creature  |           | Whether creatures shouldn't be targeted                                        |
| monster   |           | Whether monsters shouldn't be targeted                                         |
| villager  |           | Whether villagers shouldn't be targeted                                        |
| faction   |           | Whether entities in the same faction shouldn't be targeted                     |
| owner     |           | Whether the caster's owner shouldn't be targeted                               |
| vanilla   |           | Whether vanilla entities shouldn't be targeted                                 |

### Specific Filters
You can also specifically set whether to target a specific type of entity or not by using the attributes below. The effects of these attributes override the effects of the more generic target/ignore attributes for the specific entity type the attribute handles
| Attribute <!-- ETA --> | Aliases   | Description                                             | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| targetself|           | Whether to target the caster of the mechanic                         |         |
| targetplayers|        | Whether to target players                                            |         |
| targetcreative|       | Whether to target players in creative mode                           |         |
| targetspectator|      | Whether to target players in spectator mode                          |         |
| targetarmorstands|    | Whether to target armor stands                                       |         |
| targetmarkers|        | Whether to target markers                                            |         |
| targetnpcs|           | Whether to target Citizens NPCs                                      |         |
| targetanimals|        | Whether to target animals                                            |         |
| targetcreatures|      | Whether to target creatures                                          |         |
| targetsamefaction|    | Whether to target entities of the same faction                       |         |
| targetowner|          | Whether to target the caster's owner                                 |         |
| targetvanilla| targetnonmythic | Whether to target non-Mythic entities                       |         |
| targetvillagers|      | Whether to target villagers                                          |         |
| targetall |           | Whether to target everything. If this is true, all filters are ignored | false |

```yaml
  - damage{a=20} @EntitiesInRadius{r=10;targetplayers=true;targetsamefaction=true;targetowner=false}
```
> Use this to explicitly target players and entities in the same faction alongside any other valid target there may be, while also not targeting the owner of the caster

## Target Limits

All entity and location targeters also support target limits (as of v5.0.4). With this you can limit how many entities/locations are targeted, including the order in which they are selected.

This is done with the attributes:

| Attribute <!-- ETA --> | Aliases   | Description                                             | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| sort      | sortby    | How to sort the targeted entities/locations. Distance-based sorts are made against the mechanic's origin |<!--type:NONE,RANDOM,NEAREST,FURTHEST,HIGHEST_HEALTH,LOWEST_HEALTH,HIGHEST_THREAT,LOWEST_THREAT-->|
| skipTargetsUpToIndex | stuti | skips the first `n` targets of the targeter after the sort is applied, if >0 |0|
| limit     |           |The limit to the targeted entities/locations after the skip is applied, if >0 |0|


Lets say you want your ability to only target the 2 nearest players within 30 blocks. To do this, you'd simply set the limit 2 to and sort by nearest:

```yaml
  - mechanic @PlayersInRadius{r=30;limit=2;sort=NEAREST}
```

Currently, sort can have the following values:

**General sorters:**
- NONE *(usually sorts by how long the entity has existed)*
- RANDOM
- NEAREST *(to the origin of the mechanic)*
- FURTHEST *(from the origin of the mechanic)*

**Entity Only Sorters**
- HIGHEST_HEALTH
- LOWEST_HEALTH
- HIGHEST_THREAT
- LOWEST_THREAT

So the targeter will, in this order:
- Sort the targets based on the provided sort attribute, if any (and if limit and skipTargetsUpToIndex are >0)
- Skip the first n targets based on the skipTargetsUpToIndex attribute's value, if >0
- Return the first n targets based on the value of the limit attribute, if > 0

So, in essence, you can fetch target(s) at specific index(es) by using both limit and skipTargetsUpToIndex
```yaml
GiveRewards:
  Skills:
  - message{m="You are first!"} @ThreatTablePlayers{sort=HIGHEST_THREAT;limit=1} #targets the player that has the highest threat
  - message{m="You are second!"} @ThreatTablePlayers{sort=HIGHEST_THREAT;limit=1;stuti=1} #targets the player that has the second highest threat
  - message{m="You are third!"} @ThreatTablePlayers{sort=HIGHEST_THREAT;limit=1;stuti=2} #targets the player that has the third highest threat
  - message{m="You aren't on the podium!"} @ThreatTablePlayers{sort=HIGHEST_THREAT;stuti=3} #targets everyone else
``` 


<details><summary></summary>
| Attribute LTA | Aliases   | Description                                                      | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| sort      | sortby    | How to sort the targeted entities/locations. Distance-based sorts are made against the mechanic's origin |<!--type:NONE,RANDOM,NEAREST,FURTHEST-->|
| skipTargetsUpToIndex | stuti | skips the first `n` targets of the targeter after the sort is applied, if >0 |0|
| limit     |           |The limit to the targeted entities/locations after the skip is applied, if >0 |0|
</details>



<!-- LINKS -->
<!-- Single Entity Targeters -->
  [InteractionLastAttacker]: /Skills/Targeters/InteractionLastAttacker
  [InteractionLastInteract]: /Skills/Targeters/InteractionLastInteract
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
  [Children]: /Skills/Targeters/Children
  [EntitiesInRadius]: /Skills/Targeters/EntitiesInRadius
  [EntitiesInRing]: /Skills/Targeters/EntitiesInRing
  [EntitiesInRingNearOrigin]: /Skills/Targeters/EntitiesInRingNearOrigin
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
  [TrackedPlayers]: /Skills/Targeters/TrackedPlayers
<!-- ThreatTable Targeters -->
  [ThreatTable]: /Skills/Targeters/ThreatTable
  [ThreatTablePlayers]: /Skills/Targeters/ThreatTablePlayers
  [RandomThreatTarget]: /Skills/Targeters/RandomThreatTarget
  [RandomThreatTargetLocation]: /Skills/Targeters/RandomThreatTargetLocation
<!-- Single Location Targeters -->
  [CasterSpawnLocation]: /Skills/Targeters/CasterSpawnLocation
  [EscapeLocation]: /Skills/Targeters/EscapeLocation
  [Forward]: /Skills/Targeters/Forward
  [HighestBlock]: /Skills/Targeters/HighestBlock
  [Location]: /Skills/Targeters/Location
  [NearestStructure]: /Skills/Targeters/NearestStructure
  [ObstructingBlock]: /Skills/Targeters/ObstructingBlock
  [Origin]: /Skills/Targeters/Origin
  [Ownerlocation]: /Skills/Targeters/Ownerlocation
  [ParentLocation]: /Skills/Targeters/ParentLocation
  [PlayerLocationByName]: /Skills/Targeters/PlayerLocationByName
  [ProjectileForward]: /Skills/Targeters/ProjectileForward
  [SelfEyeLocation]: /Skills/Targeters/SelfEyeLocation
  [SelfLocation]: /Skills/Targeters/SelfLocation
  [SpawnLocation]: /Skills/Targeters/SpawnLocation
  [VariableLocation]: /Skills/Targeters/VariableLocation
  [TargetBlock]: /Skills/Targeters/TargetBlock
  [TargetLocation]: /Skills/Targeters/TargetLocation
  [TargetPredictedLocation]: /Skills/Targeters/TargetPredictedLocation
  [TrackedLocation]: /Skills/Targeters/TrackedLocation
  [TriggerLocation]: /Skills/Targeters/TriggerLocation
<!-- Multi Location Targeters -->
  [BlocksInPinRegion]: /Skills/Targeters/BlocksInPinRegion
  [BlocksNearOrigin]: /Skills/Targeters/BlocksNearOrigin
  [ChunksInWERegion]: /Skills/Targeters/ChunksInWERegion
  [Cone]: /Skills/Targeters/Cone
  [ForwardWall]: /Skills/Targeters/ForwardWall
  [Pin]: /Skills/Targeters/Pin
  [RandomLocationsNearOrigin]: /Skills/Targeters/RandomLocationsNearOrigin
  [RandomLocationsNearCaster]: /Skills/Targeters/RandomLocationsNearCaster
  [Rectangle]: /Skills/Targeters/Rectangle
  [RandomRingPoint]: /Skills/Targeters/RandomRingPoint
  [RingAroundOrigin]: /Skills/Targeters/RingAroundOrigin
  [Ring]: /Skills/Targeters/Ring
  [Spawners]: /Skills/Targeters/Spawners
  [Sphere]: /Skills/Targeters/Sphere
<!-- Meta Targeters -->
  [BlocksInRadius]: /Skills/Targeters/BlocksInRadius
  [BlocksInChunk]: /Skills/Targeters/BlocksInChunk
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
<!-- Special Targeters -->
  [None]: /Skills/Targeters/None
  [Region]: /Skills/Targeters/Region