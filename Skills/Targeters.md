Targeters
=========

Targeters are used to determine what a skill targets when it is fired.

While targeters are technically optional (as the default targeter will usually be @trigger), forgetting a targeter is probably one of the most common mistakes people who are new to MythicMobs make.

When a targeter is used on the Skill mechanic, all of the skills inside of the meta-skill inherit the initial targeter. You can still overwrite the parent targeter for individual mechanics inside of the meta-skill by giving them their own targeter to use.

Entity Targeters
----------------

### Single-Entity Targeters

| Targeter                             | Shorthand | Description                                                                  |
|--------------------------------------|-----------|------------------------------------------------------------------------------|
| @Self                                | @Caster   | Targets the caster of the skill                                              |
| @Target                              | @T        | Targets the mob's target                                                     |
| @Trigger                             |           | Targets the entity that triggered the skill                                  |
| @NearestPlayer{r=#}                  |           | Targets the nearest player in radius. r=5 by default                         |
| @WolfOwner                           |           | Targets the owner of the wolf                                                |
| @Owner                               |           | Targets the [owner](/skills/mechanics/setowner) of the mob                   |
| @Mount                               |           | Targets the entity that the mob is currently riding                          |
| @Parent                              |           | Targets the parent if mob was summoned by other mob.                         |
| @Children                            |           | Targets any child entities summoned by the caster.                           |
| @Passenger                           |           | Targets the rider of the mob.                                                |
| @SpawnLocation                       |           | Targets the location the world's spawn.                                      |
| @CasterSpawnLocation                 |           | Targets the location the caster spawned at.                                  |
| @PlayerByName{name="Ashijin"}        |           | Targets a specific player by name, supports placeholders. Added in 4.12      |
| @UniqueIdentifier{u="<target.uuid>"} | @UUID     | Targets a specific entity by their UUID, supports placeholders. Added in 5.0 |
| @Vehicle                             |           | Targets the Vehicle you are mounted on Added in 4.12                         |

### Multi-Entity Targeters

| Targeter                             | Shorthand         | Description                                                                                                      |
|--------------------------------------|-------------------|------------------------------------------------------------------------------------------------------------------|
| @LivingInCone{a=90.0;r=16.0;rot=0.0} | @EIC{}            | Targets all living entities in cone with angle (a), length (r), and rotation (rot) relative to facing direction  |
| @LivingInWorld                       | @EIW              | Targets all living entities in casters world                                                                     |
| @PlayersInRadius{r=#}                | @PIR{r=#}         | Targets all players in the given radius                                                                          |
| @MobsInRadius{r=#;types=X,X,X}       | @MIR{r=#;t=X,X,X} | Targets all mythicmobs or vanilla overrides of the given type in a radius                                                                   |
| @LivingEntitiesInRadius{r=#}         | @EIR{r=#;t=X,X,X} | Targets all entities in the given radius. Can accept types (for specific entities), or no type (for ANY entity). |
| @PlayersInWorld                      | @World            | Targets all players in the current world.                                                                        |
| @PlayersOnServer                     | @Server           | Targets all players in the server.                                                                               |
| @PlayersInRing{min=#;max=#}          |                   | Target all players between the specified min and max radius.                                                     |
| @PlayersNearOrigin{r=#}              |                   | Targets players near the [origin](/skills/targeters/origin) of a meta-skill.                                     |
| @MobsNearOrigin{r=#;t=X}             |                   |                                                                                                                  |
| @EntitiesNearOrigin{r=#}             | @ENO{r=#}         | Targets all entities near the [origin](/skills/targeters/origin) of a meta-skill                                                                                                                 |
| @PlayersNearTargetLocation{r=#}      | @PNTL{r=#}        | Targets all players near targetlocation. Radius=5 by default.                                                    |
| @Siblings                            |                   | Targets any mobs that share the same parent as the caster.                                                       |
| @TargetedTarget                      | @Targeted         | Targets the inherited targets.                                                                                   |
| @ItemsNearOrigin                     |                   | Targets item drops near the [origin](/skills/targeters/origin) of a meta-skill.                                  |
| @ItemsInRadius{r=#}                  |                   | Targets all item drops in the given radius                                                                       |

### ThreatTable Targeters

These targeters only work if the mob has Threat Tables enabled.

| Targeter            | Shorthand | Description                                                 |
|---------------------|-----------|-------------------------------------------------------------|
| @RandomThreatTarget | @RTT      | Targets a random entity on the threat table                 |
| @ThreatTable        | @TT       | Targets all entities on the threat table                    |
| @ThreatTablePlayers |           | Targets all players on the threat table                     |
| @RTTL               |           | Targets the location of a random target on the threat table |

Location Targeters
------------------

### Universal Attributes - Location Targeters
There are some common attributes that can be used in most of the Location Targeters

| Attribute                                | Shorthand        | Description                                                                                                      |
| ---------------------------------------- | ---------------- | ----------------------------------------- |
| Xoffset                                  | xo, x            | Centers the offset on the x axis           |
| Yoffset                                  | yo, y            | Centers the offset on the y axis           |
| Zoffset                                  | zo, z            | Centers the offset on the z axis           |
| ForwardOffset                            | foffset, fo      | Centers forward and backward offset, based on the caster's viewing angle |
| SideOffset                               | soffset, so      | Centers left and right offset, based on the caster's viewing angle |
| Rotatex                                  | rotx             | Rotation on the x axis                    |
| Rotatey                                  | roty             | Rotation on the y axis                    |
| Rotatez                                  | rotz             | Rotation on the z axis                    |
| Coordinatex                              | cx               | Sets the x axis coordinate                    |
| Coordinatey                              | cy               | Sets the y axis coordinate                    |
| Coordinatez                              | cz               | Sets the z axis coordinate                    |
| BlockTypes                               | blocktype        | Only targets selected block types. Multiple blocks can be listed by separating them using a `,` |
| BlockIgnores                             | blockignore      | Excludes selected block types from the targeter. Multiple blocks can be listed by separating them using a `,` |
| CoordinateYaw                            | cyaw             | Sets the yaw value                        |
| CoordinatePitch                          | cpitch           | Sets the pitch value                        |
| blockCentered                            |                  | Boolean value. If set to true, the center of the block at the target location will be targeted, instead of the target location itself |
| ignoretranslucent                        | it               | Boolean value. If set to true, no translucent blocks will be targeted |


### Single-Location Targeters

| Targeter                                 | Shorthand       | Description                                                                                                                                                                                                                                        |
|------------------------------------------|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| @SelfLocation{y=0.0}                     |                 | Targets the caster's location an optional yoffset                                                                                                                                                                                                  |
| @Forward{f=5;y=0.0;sideOffset=0.0;lockpitch=false}   |     | Targets a location 5 blocks infront of caster's facing direction with a yoffset and sideoffset of 0.0                                                                                                                                              |
| @ProjectileForward{f=1;rot=45}           |                 | Targets 1 block infront of the projectile offset by 45 degrees                                                                                                                                                                                     |
| @TargetLocation                          | @targetloc, @TL | Targets the mob's target's location                                                                                                                                                                                                                |
| @TriggerLocation                         |                 | Targets the location of the entity that triggered the skill                                                                                                                                                                                        |
| @Location{c=x,y,z,yaw,pitch}             |                 | The skill will target the coordinates specified.                                                                                                                                                                                                   |
| @Origin{xoffset=0;yoffset=0;zoffset=0}   |                 | Targets the location of the "origin" or "source" of a meta-skill. While that is usually the casting mob, there are special cases where this is not true (such as with the Projectile Skill, where the "origin" is the location of the projectile). |
| @Spawner{s=SpawnerName}                  |                 | Targets the location of the specified spawner(s). The string can be the name of a spawner, or a a group of spawners (using g:groupname), and also accepts wildcards (Spawner* would target Spawner1,Spawner2,Spawner3,etc)                         |
| @ObstructingBlock                        |                 | Tries to target blocks in front of the caster that are obstructing it                                                                                                                                                                              |
| @TrackedLocation                         |                 | Targets the mob's tracked location                                                                                                                                                                                                                 |
| @NearestStructure                        |                 | Targets the nearest structure's location                                                                                                                                                                                                           |

### Multi-Location Targeters

| Targeter                                                                                               | Shorthand  | Description                                                                                                                         |
|--------------------------------------------------------------------------------------------------------|------------|-------------------------------------------------------------------------------------------------------------------------------------|
| @ForwardWall{f=5;y=0.0;width=1;height=1} |                 | Targets a cube 5 blocks infront of caster's facing direction with a yoffset. can target multiple blocks depending on the width and height values                                                                                                                                                                         |
| @PlayerLocationsInRadius{r=#}                                                                          | @PLIR{r=#} | Targets all player locations in the given radius                                                                                    |
| @Ring{radius=#;points=#;xRotation=#;yRotation=#;zRotation=#;xOffset=#;yOffset=#;zOffset=#}             |            | Target points to form a ring of locations                                                                                           |
| @Cone{angle=#;points=#;range=#;rotation=#;yoffset=#}                                                   |            | Returns the # of points target locations that comprise a cone (Note: Cone is fixed on the y-axis, and cannot be rotated up or down) |
| @EntitiesInCone{angle=#;range=#;rotation=#;}                                                           |            | Targets all entities within the cone                                                                                                |
| @Sphere{radius=#;points=#;yoffset=#}                                                                   |            | Target points to form a sphere of locations                                                                                         |
| @TargetedLocation                                                                                      |            | Targets the inherited targets's location                                                                                            |
| @RingAroundOrigin{radius=#;points=#;xRotation=#;yRotation=#;zRotation=#;xOffset=#;yOffset=#;zOffset=#} | @RAO       | Targets locations in a specified ring around the origin                                                                             |

Special Targeters
-----------------

| Targeter | Shorthand | Description                                                      |
|----------|-----------|------------------------------------------------------------------|
| @None    |           | Provides no target. (Useful for mechanics with no target input.) |

The targeters below are called "meta-targeters". They target relative to an inherited targeter. For
example:

    Laser:
      Mobtype: creeper
      Display: 'Laser'
      Health: 12
      AITargetSelectors:
      - 0 clear
      - 1 players
      Skills:
      - skill{s=Laser} @target
    Laser:
      Skills:
      - ignite @EntitiesInLine{r=1}

In the example skill above, the "ignite" mechanic will target entities between the caster and the targeter specified in `- skill{s=Laser} @target`, i.e. a line between the caster and the caster's target.

Some meta-targeters also allow the mechanic to be casted "fromOrigin". This will change the starting location of the meta-targeter to be @Origin rather than the caster, which can allow for some complex effects, particularly when used with Projectiles.

| Targeter                                                                                 | Shorthand                                                       | Description                                                                                                                                                                                                     |
|------------------------------------------------------------------------------------------|-----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| @Line{radius=#;fromorigin=true/false}                                                    | @Line{r=#;fo=true/false}                                        | Targets locations between the mob and the inherited target.                                                                                                                                                     |
| @EntitiesInLine{r=#;fo=true/false}                                                       | @EIL{r=#;fo=true/false}                                         | Targets any entities in a line between the inherited target and the casting mob.                                                                                                                                |
| @LivingNearTargetLocation{radius=5}                                                      | @LNTL{r=#}                                                      | Targets all living entities near the   inherited target.                                                                                                                                                        |
| @PlayersNearTargetLocation{radius=5}                                                     | @LNTL{r=#}                                                      | Targets all players near the inherited target.                                                                                                                                                                  |
| @RLNTE{a=#;r=#;s=#;minr=#}                                                               | -                                                               | Targets random locations around the inherited target, where: a is the amount of locations, r is the radius around the inherited target, minr is the minimum radius, and s is the spacing between each location. |
| @RandomLocationsNearOrigin{a=#;r=#;s=#;minr=#}                                           | @RLNO                                                           | Targets random locations near the origin of a skill.                                                                                                                                                            |
| @FloorOfTargets                                                                          | @FOT                                                            | Targets the blocks underneath the inherited targets.                                                                                                                                                            |
| @LocationsOfTargets                                                                      | @LOT                                                            | Targets the location of the inherited targets                                                                                                                                                                   |
| @BlocksInRadius{radius=#;radiusy=#;noise=#;shape=sphere/cube;onlyair=false;noair=true}   |                                                                 | Targets all blocks in a radius of the inherited targets.                                                                                                                                                        |
| @TargetBlock                                                                           |                                                                 | Targets the block you are looking at                                                                                                                                                                            |
| @BlocksInChunk{noair=true/false;onlyair=true/false;nearorigin=true/false}                | Targets all blocks in a chunk relative to the inherited target. |
| @BlocksNearOrigin{radius=#;radiusy=#;noise=#;shape=sphere/cube;onlyair=false;noair=true} |                                                                 | Targets all blocks in a radius around the inherited target.                                                                                                                                                     |

Targeter Options
================

Target Filters
--------------

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
-   More coming later...

You can also turn off specific filters by just adding the option
**targetXXXXX** replacing XXXXX with the filter name, e.g.
**targetPlayers=false** or **targetcreative=true**

Note: As of MM 4.15 or MM 5.0, you can set the default target filters in MythicMobs/config.yml

Target Limits
-------------

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