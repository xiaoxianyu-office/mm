Random Spawns
===================

RandomSpawns give you complete control over how mobs are supposed to spawn in your worlds. You can fully customize where, how often, and how many mobs spawn, allowing for precise control over your mob spawns.

Important Differences
---------------------

There are major randomspawn options that are important to distinguish between:

-   **Action: REPLACE**
    -   The REPLACE action is used to replace mobs that are spawned by Minecraft's own random spawning system with your own mobs. 
    -   This allows for full control over Minecraft's spawning system. 
    -   If Minecraft's random spawners are turned off on your server (such as setting gamerule doMobSpawning false), this action will not do anything.

<!-- -->

-   **Action: ADD**
    -   The ADD action will utilize MythicMobs' own spawning algorithms which will, in a similar fashion to Minecraft's spawning system, generate random spawn points around players.
    -   However these spawn points, as opposed to Minecraft's, will be generated without any conditions allowing you to spawn mobs in any light level and at any location.
    -   Detailed configurations as to how these spawn points are generated can be found in MythicMobs' configuration file "config.yml".
    -   **Please note** Action: ADD only generates points around survival & adventure mode players and only if there is a location present.
    -   If a condition is used that needs an entity it will throw an exception. In case of the biome condition you can use the Biomes: option!
    -   For the Action: ADD to work, you will need to go to your plugins/MythicMobs/config.yml and set GenerateSpawnPoints to true!

<!-- -->

-   **Action: DENY**
    -   The Deny action can be used to prevent mobs from spawning.
    -   Any mob that matches the conditions of a RandomSpawn configured with DENY will not spawn.

<!-- -->

-   **Action: SCALE**
    -   *upcoming feature*

Options
-------

A complete list of all available randomspawn options.

### Global Randomspawn Options

**Example:**
```yaml
    my_favorite_randomspawn:
      Action: ADD
      Type: cute_zombie
      Level: 2
      Chance: 0.01
      Priority: 10
      UseWorldScaling: false
      Worlds: my_overworld,my_overworld_nether
      Biomes: JUNGLE,PLAINS
      Conditions:
      - day true
```
-   **Action: \[action\]**
    -   The spawning method to utilize, defaults to "ADD"
    -   Action: ADD
    -   Action: REPLACE

<!-- -->

-   **Type: \[mobtypes\]**
    -   Defines the type of mob(s) to be spawned. Can be an array/multiple mob types
    -   Type: SuperZombie
    -   Type: SkeletalMage,WitchBoss
    -   May also use vanilla mob types.

<!-- -->

-   **Level: \[number\]**
    -   The level the specified mob(s) should spawn with.
    -   Must be a fixed number, will not parse number ranges
    -   May be overriden by world scaling settings (see below for
        options)
    -   Defaults to 1
    -   Level: 7

<!-- -->

-   **Chance: \[number\]**
    -   The chance for the mob(s) to spawn.
    -   Defaults to 1 [1]
    -   **Chance: 0.025**

<!-- -->

-   **Priority: \[number\]**
    -   The priority used to determine which randomspawn to prefer when multiple mobs are chosen to be spawned at the same spawn point
    -   Rule of thumb: *a higher priority number = higher chance to be selected when multiple mobs are chosen*
    -   Defaults to 1
    -   **Priority: 128**

<!-- -->

-   **UseWorldScaling: \[true/false\]**
    -   Whether the spawned mob's level should be affected by the world scaling settings
    -   Defaults to true

<!-- -->

-   **Conditions: \[list\]**
    -   A list of conditions used to further shape the random spawn.
    -   The random spawn will fail if any of the given conditions aren't met
    -   The full list of available conditions can be found here:
        [Conditions manual page](/Skills/conditions#conditions)
    -   **Conditions:**
    -   **- condition 1**
    -   **- condition 2**
    -   **...**

<!-- -->

-   **Worlds: \[worldnames\]**
    -   The names of worlds in which the randomspawns should be applied.
    -   Can be an array / multiple worlds
    -   These names correspond to how your minecraft worlds are named in the gamefiles
    -   **Worlds: world**
    -   **Worlds: world,world\_the\_end,world\_nether**
    -   **Worlds: jays\_overworld**

<!-- -->

-   **Biomes: \[biomes\]**
    -   The biomes the specified mobtype(s) can spawn inside of.
    -   Can be an array / multiple biomes
    -   **Biomes: SNOWY\_TUNDRA,ICE\_SPIKES,SNOWY\_TAIGA,...**

<!-- -->

-   **Reason: \[reason\]**
    -   The reason of minecraft-randomspawn to be matched
    -   Can be an array / multiple reasons
    -   If this option exists, the randomspawn will only work if it matches one of the specified reasons
    -   Can be anything from this list:
        [CreatureSpawnEvent.SpawnReason](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html)
    -   **Reason: NATURAL**

<!-- -->

-   **PositionType: \[LAND/SEA\]**
    -   Whether this RandomSpawn should use land or sea points to spawn
    -   Only works with Action: ADD
    -   **PositionType: LAND**

<!-- -->

-   **Cooldown: \[number\]**
    -   The interval, in seconds, that must elapse between the spawning of two mobs by this same RandomSpawn
    -   Added in MythicMobs 5.2.0
    -   **Cooldown: 60**

### Extra Options in config.yml

These options, located in MythicMobs' "config.yml"-file, are responsible for how SpawnPoints are generated on your server. It's best to use common sense when adjusting these values, as misconfigurations of this section may cause lag on your server.

```yaml
  RandomSpawning:
    DisableVanillaSpawns: false
    GenerateSpawnPoints: true
    MaxMobsMultiplier: 1.0
    SpawnRadiusPerPlayerY: 32
    DespawnLazyRandomMobs: true
    MaxGenerationTime: 20
    PointsPerSecond:
      Land: 5
      Air: 0
      Sea: 2
      Lava: 0
      Ground: 0
```
Examples
--------

In-depth tutorial on how to create random spawners: [Creating Random
Spawners](/tutorials/randomspawns)

[1] 1 = 100 %, 0.5 = 50 % ...