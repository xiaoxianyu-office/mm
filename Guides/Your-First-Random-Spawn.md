**Difficulty: Beginner**

The [Random Spawns](/Random-Spawns) system allows you to make your custom MythicMobs spawn in your worlds, at random! You can fine tune these spawns using many options and conditions, to make them spawn however you want them to!

There are 2 actions you can use when creating your spawn, ADD and REPLACE. Using replace will make MythicMobs overwrite vanilla mob spawns, this means there will be less vanilla mobs spawning, and you will have less control over it. Add on the other hand, generates spawn points along side vanilla spawn points, meaning it doesnt affect vanilla spawns, and you have more control. 

When using add you must enable the `GenerateSpawnPoints` setting in `/plugins/MythicMobs/config/config-spawning.yml` and you must be in Survival mode or Adventure mode for mobs to spawn.

In this guide we will be using the ADD action since it is generally the better option.

Your Random Spawns go in the `/plugins/MythicMobs/RandomSpawns` folder and can also be put in subfolders for better organization. You can also create a `RandomSpawns` folder in a [pack](/Packs)


# Basic Setup
The basic setup of a RandomSpawn includes a few settings.

```yaml
SkeletonKingSpawn:
  Action: ADD
  Type: SkeletonKing
  Chance: 0.1
  Priority: 10
  Worlds: world,world_nether
```

In this basic example, we are making our mob `SkeletonKing` spawn with a 10% chance in our worlds called `world` and `world_nether`.

- `Action: ADD` we are using the [ADD](/wikis/Random-Spawns#important-differences) action to generate spawn points.
- `Type: SkeletonKing` the [Internal Name](/Mobs/Mobs#internal_name) of the MythicMob we are spawning.
- `Chance: 0.1` chance is a percentage out of 1, so 0.1 is 10%
- `Priority: 10` If we have multiple randomspawns and 2 are chosen to spawn at the same location, the one with the higher priority will spawn.
- `Worlds: world,world_nether` the mob will only spawn in these worlds, on a basic server setup this is the overworld and nether.

### Biomes

We can go further and specify the biomes our mobs spawn in too! We can do this with the Biomes option. We can add just 1 or a list of multiple biomes.

Biomes uses the [Spigot Biome Names](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/Biome.html)
```yaml
SkeletonKingSpawn:
  Action: ADD
  Type: SkeletonKing
  Chance: 0.1
  Priority: 10
  Worlds: world,world_nether
  Biomes: JUNGLE,FOREST,SOUL_SAND_VALLEY
```
In this example our mob can spawn in the worlds `world` and `nether` and only in the biomes `JUNGLE` `FOREST` and `SOUL_SAND_VALLEY`

### Position Type
When using the ADD action you can set a Position Type, this tells mythic if the mob should be spawned on land or in water.
```yaml
SkeletonKingSpawn:
  Action: ADD
  Type: SkeletonKing
  Chance: 0.1
  Priority: 10
  Worlds: world,world_nether
  Biomes: JUNGLE,FOREST,SOUL_SAND_VALLEY
  PositionType: LAND
```
Now our SkeletonKing will only spawn on land and not in oceans and rivers.

### Level
If you use the [Levels](/Mobs/Levels) system and want your mobs to spawn with a specific level, you can set that too.
```yaml
SkeletonKingSpawn:
  Action: ADD
  Type: SkeletonKing
  Level: 4
  Chance: 0.1
  Priority: 10
  Worlds: world,world_nether
```
This would spawn our mob with a level of 4.

# Adding Conditions
We can add almost any [Condition](/Skills/conditions) to our random spawn to further decide how we want our mobs to spawn. We can typically only use Entity and Location type conditions, the Replace action will check Entity conditions.

```yaml
SkeletonKingSpawn:
  Action: ADD
  Type: SkeletonKing
  Chance: 0.1
  Priority: 10
  Worlds: world,world_nether
  Biomes: JUNGLE,FOREST,SOUL_SAND_VALLEY
  Conditions:
  - night true
  - raining true
```
In this example we have added conditions to make our mob only spawn if its both night time, and raining. All the conditions in the list must be met for the mob to spawn.

**Advanced Note**

Using [Composite Conditions](/Skills/conditions#composite-conditions) you can setup conditions that would match one or the other but not both.

# Limiting
You can use conditions to limit your mob spawns and allow only certain amounts of your mobs to spawn. The 2 most common ways to do this is using the [MobsInRadius](/skills/conditions/mobsinradius) and [MobsInChunk](/skills/conditions/mobsinchunk) conditions.
```yaml
SkeletonKingSpawn:
  Action: ADD
  Type: SkeletonKing
  Chance: 0.1
  Priority: 10
  Worlds: world,world_nether
  Biomes: JUNGLE,FOREST,SOUL_SAND_VALLEY
  Conditions:
  - night true
  - raining true
  - mobsinchunk{a=<10} true
  - mobsinradius{t=SkeletonKing;a=<3;r=64} true
```
In this example we are allowing our SkeletonKing to spawn only if there is less than 10 of *any* mob in the chunk, and less than 3 SkeletonKings within a 64 block radius.

# Scaling
This section only applies if your mobs have [Level Modifiers](/Mobs/Levels) setup.

We can use [WorldScaling](/Mobs/Levels#world-scaling) to determine if the mobs level should be increased based on the distance. By default this is enabled, so if your mobs have level modifiers, and you *don't* want them to increase in level based on the world scaling, set this to false.
```yaml
SkeletonKingSpawn:
  Action: ADD
  Type: SkeletonKing
  Chance: 0.1
  Priority: 10
  Worlds: world,world_nether
  UseWorldScaling: false
```