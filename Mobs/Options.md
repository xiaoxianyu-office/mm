All options available when creating a mob. Most of these options go under the `Options` section, like so:
```yml
Dummy:
  Type: skeleton
  Options:
    MovementSpeed: 0.3
    PreventSunburn: true
```

## Universal options

These options are universal and will work regardless of the mob type.

#### AlwaysShowName
Whether the name-tag is always displayed.
Equivalent to the NBT-tag `CustomNameVisible`.
Defaults to `false`.
```yml
Options:
  AlwaysShowName: false
```

<!--
**AttackSpeed: \[number\]**

      * Sets the attack speed of the mob.
      * Defaults to vanilla attack speed for the respective mobs. (Doesn't do anything.)
-->

#### Invisible
Sets the permanent invisibility effect on the mob; no need to apply invisibility potion with `~onSpawn` trigger.
Defaults to `false`.
```yml
Options:
  Invisible: true
```

#### Collidable
Whether the mob has collisions. Collisions in Minecraft are bidirectional, so this would need to be set to `false` on both
the entity colliders to ensure that no collisions takes place but will also stop the player from pushing the mob. Defaults to `true`.
```yml
Options:
  Collidable: true
```

#### DigOutOfGround
Teleports the mob two blocks up if it takes `SUFFOCATION` damage. Defaults to `false`.
```yml
Options:
  DigOutOfGround: false
```

#### Despawn
Determines how the mob will despawn.
This option should be turned on if you're using a lot of mob spawners or entities will overwhelm your server.
Defaults to `true`.

Available values:
- `true` - despawns the mob if there are no nearby players, on chunk unload.
- `false` - similar to `persistent` but can be despawned.
- `chunk` - despawns the mob when the chunk unloads.
- `persistent` - the mob is persistent and doesn't despawn. To remove a persistent mob, you have to either use the kill command (`/mm m kill <type>`) or append the `-p` flag to the killall one (`/mm m killall -p`). More information on the subject can be found [here](/Commands-and-Permissions#mob-commands).
```yml
Options:
  Despawn: true
```

#### FollowRange
The range in blocks within which a mob will target to attack or track an entity.
Defaults to vanilla follow range - `32`.
```yml
Options:
  FollowRange: 32
```

#### Glowing
Sets whether the mob is permanently glowing. Defaults to `false`.
```yml
Options:
  Glowing: false
```

#### HealOnReload
Allows non-respawning mobs to heal once the chunk they are in gets reloaded. Defaults to `false`.
```yml
Options:
  HealOnReload: false
```


#### Invincible
Makes the mob completely invincible to all types of damage. This option cannot be changed by command skills.
Defaults to `false`.
```yml
Options:
  Invincible: false
```

#### Interactable
Sets whether the mob can be interacted with. If the mob is an armor stand, it will deny any interaction with the equipments.
Defaults to `false`.
```yml
Options:
  Interactable: false
```

#### LockPitch
Keeps the mob's head from looking up/down. Requires [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/).
Defaults to `false`.
```yml
Options:
  LockPitch: false
```

#### KnockbackResistance
A percentage of knockback resisted from attacks. This option can be anywhere between `0` and `1`.
But a mob with 100% knockback resistance can still be knocked back by a bow's enchantment: `ARROW_KNOCKBACK` (punch enchantment).
For true knockback resistance, see the [velocity](/Skills/mechanics/velocity) mechanic page. Defaults to `0`.
```yml
Options:
  KnockbackResistance: 0.5
```

#### MaxCombatDistance
Prevents players that are a number of blocks away from damaging the mob.
Setting this option to a number less than the distance of a certain mob skill or attack will ensure that the mob can damage the player and will not be as easy to exploit.
Defaults to `256`.
```yml
Options:
  MaxCombatDistance: 256 
```

#### MovementSpeed
The movement speed of the mob.
Most mobs has a default move speed of `0.2` and any value higher than `1` tends to make a mob difficult or impossible to fight.
```yml
Options:
  MovementSpeed: 0.2
```

#### NoAI
Whether the mob should have AI. This option overrides any AI goals specified in [AIGoalSelectors](/Mobs/Mobs#aigoalselectors).
As opposed to AIGoalSelectors, this will work on entities that have hardcoded AI. And if this is set to `true`, the mob will never cast any skills.
Defaults to `false`.
```yml
Options:
  NoAI: false
```

#### NoDamageTicks
Defines how long in ticks the mob is invulnerable after taking damage.
If [ImmunityTables](/Mobs/ImmunityTables) is enabled for the mob, then `NoDamageTicks` will be per player instead of global.
Defaults to `10`.
```yml
Options:
  NoDamageTicks: 20
```

#### NoGravity
Whether the mob should not have gravity. If set to `true`, the mob **CANNOT** have the [velocity](/Skills/mechanics/velocity) mechanic used on it.
Defaults to `false`.
```yml
Options:
  NoGravity: false
```

#### PassthroughDamage
Causes all damage taken to be redirected to the mob's parent, if one exists. A mob's parent is the entity that initially summoned the mob.
Defaults to `false`.
```yml
Options:
  PassthroughDamage: false
```

#### PreventItemPickup
Prevent mobs from picking up items;
Defaults to `true`.
```yml
Options:
  PreventItemPickup: false
```

#### PreventLeashing
Whether to prevent a leash from being placed on the mob.
Defaults to `true`.
```yml
Options:
  PreventLeashing: false
```

#### PreventMobKillDrops
Prevents a MythicMob's target from dropping loot.
Defaults to `false`.
```yml
Options:
  PreventMobKillDrops: false
```

#### PreventOtherDrops
Prevents the mob from dropping its vanilla loot table.
Defaults to `false`.
```yml
Options:
  PreventOtherDrops: false
```

#### PreventRandomEquipment
Prevents the mob from spawning with random equipment.
Defaults to `false`.
```yml
Options:
  PreventRandomEquipment: false
```

#### PreventRenaming
Prevents the mob from being renamed using a nametag.
Defaults to `true`.
```yml
Options:
  PreventRenaming: false
```

#### PreventSunburn
Prevents the mob from burning in the sun.
Defaults to `false`.
```yml
Options:
  PreventSunburn: false
```

#### RepeatAllSkills
Whether to repeat HP based skills if a mob heals back above the health threshold.
Defaults to `false`.
```yml
Options:
  RepeatAllSkills: false
```

#### ReviveHealth
When the mob's death event gets cancelled (via a [Cancelevent](/skills/mechanics/cancelevent) mechanic [~onDeath](/Skills/Triggers#ondeath)) the one specified is the amount of health the mob's will be set to. If the value is `-1`, the mob will heal to its own max health value.
```
#This mob will always return to 50 health every time the death event is cancelled
ExampleMob:
  Type: COW
  Health: 100
  Options:
    ReviveHealth: 50
  Skills:
  - cancelevent{sync=true} @self ~onDeath
```
```
#This mob will always return to its maximum health (100) every time the death event is cancelled
ExampleMob:
  Type: COW
  Health: 100  
  Options:
    ReviveHealth: -1
  Skills:
  - cancelevent{sync=true} @self ~onDeath
```

#### ShowHealth
Displays the health of the mob through messages broadcast within a radius and formatting by `Mobs.ShowHealth.Radius` and `Mobs.ShowHealth.Formatting`, respectively, in `/plugins/MythicMobs/config.yml`
Defaults to `false`.
```yml
Options:
  ShowHealth: false
```

#### Silent
Whether a mob should use vanilla sound effects.
Defaults to `false`. 
```yml
Options:
  Silent: false
```

------------------------------------------------------------------------

## Mob specific options

These are specific mob options and will have no effect when used on a
different mob type.

### Armor Stands

#### CanMove: \[true/false\]**
Sets whether an armor stand can move. Defaults to `true` and requires PaperSpigot
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    CanMove: true
```

#### CanTick
Sets whether an armor stand can tick. Defaults to `true` and requires PaperSpigot
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    CanTick: true
```

#### HasArms
Sets whether an armor stand has arms. Defaults to `false`.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    HasArms: true
```

#### HasBasePlate
Sets whether an armor stand has a baseplate. Defaults to `true`
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    HasBasePlate: true
```

#### HasGravity
Sets whether the armor stand is affected by gravity. Defaults to `true`.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    HasGravity: true
```

#### Invisible
Sets whether the armor stand is invisible. Defaults to `false`.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    Invisible: true
```

#### ItemBody
Designates the [Mythic Item](/Items/Items) that should go in the body/chest slot of an armor stand.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    ItemBody: AN_EXAMPLE_CHESTPLATE
```

#### ItemFeet
Designates the [Mythic Item](/Items/Items) that should go in the feet slot of an armor stand.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    ItemFeet: AN_EXAMPLE_BOOTS
```

#### ItemHand
Designates the [Mythic Item](/Items/Items) that should go in the main hand slot of an armor stand.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    ItemHand: AN_EXAMPLE_SWORD
```

#### ItemOffhand
Designates the [Mythic Item](/Items/Items) that should go in the off hand slot of an armor stand.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    ItemOffhand: AN_EXAMPLE_STICK
```

#### ItemHead
Designates the [Mythic Item](/Items/Items) that should go in the helmet slot of an armor stand.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    ItemHead: AN_EXAMPLE_HELMET
```

#### ItemLegs
Designates the [Mythic Item](/Items/Items) that should go in the leggings slot of an armor stand.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    ItemLegs: AN_EXAMPLE_PANTS
```

#### Marker
Sets the armor stand as a marker. This option prevents the armor stand from being destroyed in game,
making it completely non-interactable. Defaults to `false`.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    Marker: false
```

#### Small
Sets the armor stand to small variant. Defaults to `false`.
```yml
Dummy:
  Type: ARMOR_STAND
  Options:
    Small: true
```

#### Pose
Sets the body part's current pose.
Default values are `0,0,0` and accepts ranges like `#to#`.
These will go under the `Pose` section instead of the `Options` section.
###### Head
```yml
Mob:
  Type: armor_stand
  Pose:
    Head: 0,50,0
```
###### Body
```yml
Mob:
  Type: armor_stand
  Pose:
    Body: 0,10,10
```
###### LeftArm
```yml
Mob:
  Type: armor_stand
  Pose:
    Body: 0to360,0,0
```
###### RightArm
```yml
Mob:
  Type: armor_stand
  Pose:
    RightArm: 0to90,0,0
```
###### LeftLeg
```yml
Mob:
  Type: armor_stand
  Pose:
    LegLeg: 0,0to80,0
```
###### RightLeg
```yml
Mob:
  Type: armor_stand
  Pose:
    RightLeg: 20,25,0
```

#### Bees

**Anger: \[number\]**

      * Sets the time in ticks until bee anger ends.
      * If set to 0 the bee will not be angry.
      * Defaults to 0.

**HasNectar: \[true/false\]**

      * Whether the bee is carrying pollen.
      * Defaults to false.

**HasStung: \[true/false\]**

      * Whether the bee has stung an entity.
      * Defaults to false.

#### Cat

**CatType: \[type\]**

     * Sets the type of cat
     * Types can be ALL_BLACK, BLACK, BRITISH_SHORTHAIR, CALICO, PERSIAN, JELLIE, RAGDOLL, RED, SIAMESE, TABBY or WHITE.

**CollarColor: \[color\]**

     * Sets the color of the cat's collar.
     * Available colors are: BLACK, BLUE, BROWN, CYAN, GRAY, GREEN, LIGHT_BLUE, LIGHT_GRAY, LIME, MAGENTA, ORANGE, PINK, PURPLE, RED, WHITE, or YELLOW.

#### Chicken

**Jockey: \[true/false\]**

      * Wether or not the chicken is a chickenjockey.
      * Doesn't really do anything, but it's nice to have options.
      * Defaults to false.

#### Creepers

**ExplosionRadius: \[number\]**

      * Sets the radius/power of the creepers explosion
      * Defaults to 3

**FuseTicks: \[number\]**

      * Sets the number of ticks it takes for creepers to explode.
      * Defaults to 30

**SuperCharged: \[true/false\]**

      * Wether the creeper should spawn as a super charged creeper.
      * Defaults to false.

**PreventSuicide: \[true/false\]**

      * Prevents creepers from dying upon exploding. Set `mobGriefing` gamerule to true for this option to work.
      * Defaults to false.

#### Enderman

**PreventTeleport: \[true/false\]**

      * Meant for Endermen but //might// work on other mobs. May break teleport skills!
      * Defaults to false.

**HeldBlock: `[Material]`**

      * Sets the block that the Enderman is carrying.

#### Experience_orb

**Experience: \[Number\]**

      * Sets the amount of experience give by the experience orb mob.
      * Defaults to 1

#### Falling Blocks

**Block: \[Material type\]**

      * Determines the type of the block.
      * Defaults to STONE

**BlockData: \[Number\]**

      * Additional field for inputting blockdata.
      * Defaults to 0

**DropsItem: \[true/false\]**

      * Drops the falling block's item.
      * Defaults to true

**HurtsEntities: \[true/false\]**

      * Damages entities on impact.
      * Defaults to true

#### Fox

**FoxType: \[Entity type\]**

      * Determines the type of the fox. 
      * Can be RED or SNOW
      * Defaults to RED

#### Frog
**Type: \[Entity type\]**

      * Determines the type of the Frog
      * Can be WARM, COLD or TEMPERATE

#### Hoglin

**ImmuneToZombification: \[true/false\]**

      * Whether or not the hoglin is immune to being zombified
      * Defaults to false

**Huntable: \[true/false\]**

      * Whether the hoglin is able to be hunted by piglins.
      * Defaults to true

#### Horses, Donkeys, and Mules

**HorseArmor: \[armor\_type\]**

      * Used for horses to set the type of armor they have on.
      * Can be iron, gold, or diamond
      * [armor_type] must be in lower case

**CarryingChest: \[true/false\]**

      * Used for donkeys to set whether they are carrying a chest or not.
      * Defaults to false.

**HorseColor: \[horse\_color\]**

      * Sets color of the horse
      * Colors Must be uppercase,can be BLACK, BROWN, CHESTNUT, CREAMY, DARK_BROWN, GRAY or WHITE

**Saddled: \[true/false\]**

      * Used for horses to set whether they are saddled or not.
      * Defaults to false.

**HorseStyle: \[horse\_style\]**

      * Sets the style of the horse.
      * Styles can be BLACK_DOTS, WHITE, WHITE_DOTS, WHITEFIELD, NONE

**Tamed: \[true/false\]**

      * Used for horses to set whether they are tamed or not.
      * Defaults to false.

**HorseType: \[type\]**

      * Defines the type of horse
      * Can be UNDEAD_HORSE, SKELETON_HORSE, MULE, DONKEY or HORSE
      * Defaults to HORSE
      * Removed in MC 1.11+, use [[databases/mobs/types|mob type]] instead.

#### Iron Golem

**PlayerCreated: \[true/false\]**

      * Acts as if the player built the mob.
      * Defaults to false.

#### Panda

**MainGene: \[Gene Type\]**

      * Sets the main gene that the panda can pass on to it's offspring.
      * Can be NORMAL, AGGRESSIVE, LAZY, WORRIED, PLAYFUL, WEAK, BROWN
      * Defaults to NORMAL

**HiddenGene: \[Gene Type\]**

      * Sets the hidden gene that the panda can pass on to it's offspring.
      * Can be NORMAL, AGGRESSIVE, LAZY, WORRIED, PLAYFUL, WEAK, BROWN
      * Defaults to NORMAL

#### Piglin

**AbleToHunt: \[true/false\]**

      * Whether or not the piglin is able to hunt
      * Defaults to false

**ImmuneToZombification: \[true/false\]**

      * Whether or not the piglin is immune to being zombified
      * Defaults to false

#### Piglin Brutes

**ImmuneToZombification: \[true/false\]**

      * Whether or not the piglin is immune to being zombified
      * Defaults to false

#### Pigs

**Saddled: \[true/false\]**

      * Wether or not the pig spawns with a saddle.
      * Defaults to false

#### Rabbits

**RabbitType: \[rabbit\_type\]**

      * Sets type of rabbit
      * Types can be BLACK, BLACK_AND_WHITE, BROWN, GOLD, SALT_AND_PEPPER, THE_KILLER_BUNNY or WHITE

**Baby: \[true/false\]**

      * Not sure why this exists.
      * Defaults to false.

**IsKillerBunny: \[true/false\]**

      * Sets the rabbit as the Killer Bunny.

#### Sheep

**Sheared: \[true/false\]**

      * Sheep is already sheared.
      * Defaults to false.

#### Silverfish

**PreventBlockInfection: \[true/false\]**

      * Prevent silverfish from infecting blocks.
      * Defaults to true.

#### Snow Golem

**Derp: \[true/false\]**

      * Snow Golem is already sheared pumpkin
      * Defaults to false.

**PreventSnowFormation: \[true/false\]**

      * Prevent snowmen from creating snow.
      * Defaults to false.

#### TNT

**FuseTicks: \[number\]**

      * How long the TNT takes to explode
      * Defaults to -1 (instantly)

**ExplosionYield: \[number\]**

      * Determines the strength of the explosion
      * Defaults to -1 (none)

**Incendiary: \[true/false\]**

      * Wether the explosion is capable of starting fires
      * Defaults to false

#### Tropical Fish

**Pattern: \[type\]**

      * Sets the shape of the fish
      * Types can be BETTY, BLOCKFISH, BRINELY, CLAYFISH, DASHER, FLOPPER, GLITTER, KOB, SNOOPER, SPOTTY, STRIPEY, or SUNSTREAK.

**BodyColor: \[color\]**

      * Sets the primary color of the fish
      * Color can be BLACK, BLUE, BROWN, CYAN, GRAY, GREEN, LIGHT_BLUE, LIGHT_GRAY, LIME, MAGENTA, ORANGE, PINK, PURPLE, RED, WHITE, or YELLOW.

**PatternColor: \[color\]**

      * Sets the secondary color of the fish
      * Color can be BLACK, BLUE, BROWN, CYAN, GRAY, GREEN, LIGHT_BLUE, LIGHT_GRAY, LIME, MAGENTA, ORANGE, PINK, PURPLE, RED, WHITE, or YELLOW.

#### Villagers

**HasTrades: \[true/false\]**

      * Villager can be traded with.
      * Defaults to false.
Check out [Trades](/Mobs/Mobs#trades)

**Profession: \[profession\]**

      * Specifies the profession of the villager type mob.
      * Can be ARMORER, BUTCHER, CARTOGRAPHER, CLERIC, FARMER, FISHERMAN, FLETCHER, LEATHERWORKER, LIBRARIAN, MASON, NITWIT, NONE, SHEPHERD, TOOLSMITH, WEAPONSMITH.
      * Villagers without this option will roll a random profession on their initial spawn.
      * Examples:
        Profession: MASON

**Type: \[type\]**

      * Represents Villager type, usually corresponding to what biome they spawn in.
      * Can be DESERT, JUNGLE, PLAINS, SAVANNA, SNOW, SWAMP, TAIGA.
      * Defaults to PLAINS.
      * Examples:
        Type: PLAINS

**Level: \[level\]**

      * Villager profession level, levels 1 - 5.
      * Level 1 villagers might switch professions. If you want a villager to hold its profession, give them a level of 2 or higher.
      * Required if setting villager professions.
      
#### Zombies (all variants)

**PreventJockeyMounts: \[true/false\]**

      * Sets whether the zombie will spawn as a jockey.
      * Only works for Zombies.
      * Defaults to false.

**PreventTransformation: \[true/false\]**

      * Sets whether zombies can be turned into pigmen/drowned.
      * Only works for Zombies.
      * Defaults to true.

**ReinforcementsChance: \[number\]**

      * Chance for zombies to spawn reinforcements on taking damage.
      * Should be a number between 0 and 1 (0% and 100% chance)
      * Only works for Zombies.
      * Defaults to 0.

#### Zombie Villagers

**Profession: \[type\]**

      * Sets the type of the villager the zombie should represent.
      * This option will also make the zombie turn into the respective villager type when being cured using potions.
      * Can be `ARMORER, BUTCHER, CARTOGRAPHER, CLERIC, FARMER, FISHERMAN, FLETCHER, LEATHERWORKER, LIBRARIAN, MASON, NITWIT, NONE, SHEPHERD, TOOLSMITH, WEAPONSMITH.`

------------------------------------------------------------------------

### Group specific options

#### Breedable mobs

**Age: \[number\]**

      * -1 for Baby. 1 for Adults
      * What the age of the mob will be.
      * Usable on any mob that can age. For example: Sheep, Pigs, Cows...
      * Defaults to 1.
      * Use very low negative numbers to mess with the mobs model (not supported)
      * May not be working properly

**AgeLock: \[true/false\]**

      * Whether the mobs age should be locked in place.
      * Useful for keeping a baby mob from growing up over time.
      * Defaults to false
      * This is required if you want Age option to work

**Baby: \[true/false\]**

      * Sets baby/adult status of mob.
      * Use if **Age: [number]** does not work.

#### Colorable Mobs

Used for sheep and wolves.

**Color: \[number\]**

      * Sets the wool color of sheep or the collar color of wolves
      * **The string is the name of the color you want. Ex: Color: RED**
      * [[http://minecraft.gamepedia.com/Wool|http://minecraft.gamepedia.com/Wool]]

#### Neutral mobs

Used for wolves and zombie pigmen.

**Angry: \[true/false\]**

      * Whether the mob will spawn angry or not.
      * **Note: Due to a Bukkit/Spigot bug wolves can not be spawned angry with this option.**
      * **Use AIGoalSelectors and AITargetSelectors if you want to spawn angry wolves.**

#### Slimes & Magma Cubes

**PreventSlimeSplit: \[true/false\]**

      * Prevents slimes and magmacubes from splitting.
      * Default to false

**Size: \[number\]**

      * Sets the size of slimes, magma cubes, and phantoms.
      * Can get VERY big and get exponentially larger with each increase.
      * Extremely high size will cause server lag and possibly crashes.
      * Default to 1to8(Phantoms is 1)

#### Tameable Mobs

**Tameable: \[true/false\]**

      * Allows players to tame the mobs. Used for wolves, cats and horses.
      * Defaults to false.

------------------------------------------------------------------------