Introduction
------------

Conditions are used to determine whether or not an action may execute.

Conditions can be used in [1]:
-   [Skill Mechanics](/skills/mechanics/skill)
-   [Drop Tables](/Items/Drops#drop-tables)
-   [Spawners](/Spawners)
-   [Random Spawners](/Random%20Spawns)

When applying multiple conditions, all of them must be met in order for the skill to be executed. Some conditions allow arrays that can be split by commas. Such conditions only require one of the strings in the array to match.

To see how to use the premium only in-line conditions, [click here!](/skills/conditions/in-linetargetconditions)

Usage
-----

### Types

  
Conditions can be broken into three types:

1. Entity Conditions: These check the conditions of an entity.
2. Location Conditions: These check the conditions at a location. If a location condition is used while an entity is targeted, it will check the conditions at the entity's location.
3. Compare conditions: These check for certain conditions between two different "things". For example, "Cuboid" will return true if a target is within a cube where the corners are two coordinates, while "StringEquals" will return true or false depending on whether two strings match.

Conditions can also be used in three different places within a meta skill:

1. Conditions: Conditions in this section check the conditions of the caster or the caster's location.
2. TargetConditions: Conditions in this section check the conditions of the target or target location inherited from the skill's targeter.
3. TriggerConditions: Conditions in this section check the conditions of the entity that triggered the skill.

### Examples
```
Conditions:
- globalscore{objective=Test;v=>10}
```
In the example above, the globalscore condition will check the caster's global score.
```
TargetConditions:
  - globalscore{objective=Test;v=>10}
```
The example above uses the exact same condition, but here the globalscore condition will check the inherited target's global score. Since globalscore is an entity condition, it will only work if an entity is targeted.

**Format**:
```
SkillName:
  Conditions:
    - condition [variable]
  TargetConditions:
    - condition [variable] [action]
  TriggerConditions:
    - condition [variable] [action] [action_variable]
    - condition{variable1=value;variable2=value} [action] [action_variable]
```

These new "actions" control how the skill acts when a condition is met
or not met. Here are some examples:
```
YourAwesomeSkill:
  Conditions:
    - day required
  TargetConditions:
    - stance defensive power 0.5
  TriggerConditions:
    - stance{stance=defensive} power 0.5
    - score{objective=test;value=>20} cancel
    - haspotioneffect{type=POISON;level=>0;duration=0to100} true
```
**Ranged Values:**  
Ranged values use either the format **#to#** or **#-#**. You must use "to" instead of "-" if you want to use negative numbers in the range. For:
```
YourMagnificentSkill:
  Conditions:
    - altitude{a=1-5}
  TargetConditions:
    - distance{d=1to10} true
  TriggerConditions:
    - distance{d=1to10} true
```
Condition Actions
-----------------

Condition Actions allow you to do additional things based off of conditions. The default condition action is **true**

| Action                     | Description                                                                |
|----------------------------|----------------------------------------------------------------------------|
| **required** (or **true**) | The condition is required for the skill to run.                            |
| **cancel** (or **false**)  | The skill will not run if this condition is met.                           | **Level** | |
| **power [multiplier]**     | Modifies the skill's power (e.i. power 2.0 would double the skill's power) |
| **cast [skill]**           | Casts an additional skill if the condition is met.                         |
| **castinstead [skill]**    | Casts a different skill instead if the condition is met.                   |
| **orElseCast [skill]**     | Casts a different skill instead if the condition is not met. (4.12 MM)     |

Conditions
----------

| Condition                                                                     | Type     | Description                                                                                 |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------|
| [Altitude](/skills/conditions/altitude)                                       | Entity   | Tests how far above the ground the target entity is                                         |
| [Biome](/skills/conditions/biome)                                             | Location | Tests if the target is within the given list of biomes                                      |
| [BiomeType](/skills/conditions/biometype)                                     | Location | Tests for the biome category at a location.
| [BlockType](/skills/conditions/blocktype)                                     | Location | Tests the material type present at the target location                                      |
| [Blocking](/skills/conditions/blocking)                                       | Entity   | Tests if the targeted player is blocking with a shield                                      |
| [BowTension](/skills/conditions/bowtension)                                   | Meta     | Checks the bow tension of when an entity shoots from a bow                                  |
| [Burning](/skills/conditions/burning)                                         | Entity   | Whether or not the target entity is on fire                                                 |
| [Chance](skills/conditions/chance)                                            | Meta     | The chance that the metaskill has to be executed
| [Children](/skills/conditions/children)                                       | Entity   | Tests how many children the caster has                                                      |
| [Color](/skills/conditions/color)                                             | Entity   | Tests the entity's colors                                                                   |
| [Crouching](/skills/conditions/crouching)                                     | Entity   | Whether or not the target entity is crouching                                               |
| [Cuboid](/skills/conditions/cuboid)                                           | Compare  | Whether the target is within the given cuboid between location1 x location2                 |
| [DamageAmount](/skills/conditions/DamageAmount)                               | Entity   | Checks for a range of damage taken                                                          |
| [DamageCause](/skills/conditions/DamageCause)                                 | Entity   | Checks the type of the damage cause                                                         |
| [Dawn](/skills/conditions/dawn)                                               | Location | If the time is dawn, from 22000 to 2000 in-game time                                        |
| [Day](/skills/conditions/day)                                                 | Location | If the time is day, from 2000 to 10000 in-game time                                         |
| [Distance](/skills/conditions/distance)                                       | Compare  | Whether the distance between the caster and target is within the given range                |
| [DistanceFromTrackedLocation](/skills/conditions/distancefromtrackedlocation) | Location | Whether the distance from the tracked location to the target is within the given range      |
| [DistanceFromSpawn](/skills/conditions/distancefromspawn)                     | Location | Whether the distance from the world's spawn point to the target is within the given range   |
| [Dusk](/skills/conditions/dusk)                                               | Location | If the time is dusk, from 14000 to 18000 in-game time.                                      |
| [EnchantingLevel](/skills/conditions/enchantingLevel)                         | Entity   | Checks the entity experience level                                                          |
| [EnderDragonPhase](/skills/conditions/EnderDragonPhase)                       | Entity   | Checks if the ender dragon is in a phase or phases                                          |
| [EntityType](/skills/conditions/entitytype)                                   | Entity   | Tests the entity type of the target                                                         |
| [Faction](/skills/conditions/faction)                                         | Entity   | Tests for the targets faction                                                               |
| [FallSpeed](/skills/conditions/fallspeed)                                     | Entity   | If the fall speed of the target is within the given range                                   |
| [FieldOfView](/skills/conditions/fieldofview)                                 | Compare  | Tests if the target is within the given angle from where the caster is looking              |
| [FoodLevel](/skills/conditions/FoodLevel)                                     | Entity   | Checks if the target has food within the range                                              |
| [FoodSaturation](/skills/conditions/FoodSaturation)                           | Entity   | Checks if the target has food within the range                                              |
| [Gliding](/skills/conditions/gliding)                                         | Entity   | If the target is gliding                                                                    |
| [GlobalScore](/skills/conditions/globalscore)                                 | Entity   | Checks a global scoreboard value                                                            |
| [HasAura](/skills/conditions/hasaura)                                         | Entity   | Checks if the target entity has the given aura                                              |
| [HasAuraStacks](/skills/conditions/hasaurastacks)                             | Entity   | Tests if the target has the given range of stacks from an aura                              |
| [HasCurrency](/skills/conditions/hascurrency)                                 | Entity   | If the target has the given amount of vault currency                                        |
| [HasInventorySpace](/skills/conditions/hasinventoryspace)                     | Entity   | If the target has the given amount of empty inventory space                                 |
| [HasItem](/skills/conditions/hasItem)                                         | Entity   | Tests if the target player has the given number of given material                           |
| [HasOwner](/skills/conditions/hasowner)                                       | Entity   | Tests if the target mob has an owner                                                        |
| [HasParent](/skills/conditions/hasparent)                                     | Entity   | Tests if the target mob has a parent                                                        |
| [HasPassenger](/skills/conditions/hasPassenger)                               | Entity   | Checks if the target entity has a passenger                                                 |
| [HasGravity](/skills/conditions/hasgravity)                                   | Entity   | Tests if the target mob has gravity                                                         |
| [HasPotionEffect](/skills/conditions/haspotioneffect)                         | Entity   | Tests if the target entity has a potion effect                                              |
| [HasTag](/skills/conditions/hastag)                                           | Entity   | Tests if the target has a scoreboard tag                                                    |
| [HasPermission](/skills/conditions/haspermission)                             | Entity   | Tests if the target player has a permission                                                 |
| [Health](/skills/conditions/health)                                           | Entity   | Matches the target's health                                                                 |
| [Height](/skills/conditions/height)                                           | Location | Checks if the target's Y location is within a range                                         |
| [HeightAbove](/skills/conditions/heightabove)                                 | Location | Checks if the target's Y location is above a value                                          |
| [HeightBelow](/skills/conditions/heightbelow)                                 | Location | Checks if the target's Y location is below a given value                                    |
| [Holding](/skills/conditions/holding)                                         | Entity   | Checks if the target is holding a given material(support MythicMobs and MMOItems)           |
| [InBlock](/skills/conditions/inblock)                                         | Location | Checks the material at the target location                                                  |
| [InCombat](/skills/conditions/incombat)                                       | Entity   | If the target mob is considered in combat                                                   |
| [Inside](/skills/conditions/inside)                                           | Location | Checks if the target has a block over their head                                            |
| [isCaster](/skills/conditions/iscaster)                                       | Entity   | Checks if the target is the caster                                                          |
| [isChild](/skills/conditions/ischild)                                         | Entity   | Checks if the target is a child of the caster                                               |
| [isFlying](/skills/conditions/isflying)                                       | Entity   | Checks if the target player is flying
| [isLiving](/skills/conditions/isliving)                                       | Entity   | Checks if the target is a living entity                                                     |
| [isLeashed](/skills/conditions/isleashed)                                     | Entity   | Checks if the target has been leashed                                                       |
| [isMonster](/skills/conditions/ismonster)                                     | Entity   | Checks if the target is a monster                                                           |
| [isPlayer](/skills/conditions/isplayer)                                       | Entity   | Checks if the target is a player                                                            |
| [isSprinting](/skills/conditions/issprinting)                                 | Entity   | Checks if the target **Player** is sprinting                                                |
| [ItemIsSimilar](/skills/conditions/itemissimilar)                             | Entity   | Checks that targeted player's inventory slot if it's similar to an item                     |
| [ItemRecharging](/skills/conditions/itemrecharging)                           | Entity   | Checks if the target's weapon is recharging                                                 |
| [LastDamageCause](/skills/conditions/lastdamagecause)                         | Entity   | Checks the target's last damage cause                                                       |
| [LastSignal](/skills/conditions/lastsignal)                                   | Entity   | Matches the last signal received by the target mob                                          |
| [Level](/skills/conditions/level)                                             | Entity   | Checks the target MythicMob's level                                                         |
| [LightLevel](/skills/conditions/lightlevel)                                   | Location | Tests the light level at the target location                                                |
| [LineOfSight](/skills/conditions/lineofsight)                                 | Compare  | Tests if the target is within line of sight of the caster                                   |
| [LunarPhase](/skills/conditions/lunarphase)                                   | Location | Checks the target world's lunar phase                                                       |
| [MobsInRadius](/skills/conditions/mobsinradius)                               | Location | Checks how many mobs are in a given radius                                                  |
| [MobsInChunk](/skills/conditions/mobsinchunk)                                 | Location | Matches a range to how many mobs are in the target location's chunk                         |
| [MobsInWorld](/skills/conditions/mobsinworld)                                 | Location | Matches a range to how many mobs are in the target world                                    |
| [MotionX](/skills/conditions/motionx)                                         | Entity   | Checks the X motion of the target entity against a range.                                   |
| [MotionY](/skills/conditions/motiony)                                         | Entity   | Checks the Y motion of the target entity against a range.                                   |
| [MotionZ](/skills/conditions/motionz)                                         | Entity   | If the target has a velocity greater than zero                                              |
| [Mounted](/skills/conditions/mounted)                                         | Entity   | If the target entity is riding a mount/vehicle                                              |
| [Moving](/skills/conditions/moving)                                           | Entity   | If the target has a velocity greater than zero                                              |
| [MythicMobType](/skills/conditions/mythicmobtype)                             | Entity   | Checks the MythicMob type of the target mob                                                 |
| [Name](/skills/conditions/name)                                               | Entity   | Checks against the entity's name                                                            |
| [NearClaim](/skills/conditions/nearclaim)                                     | Location | If the target location is near any GriefPrevention claims                                   |
| [Night](/skills/conditions/night)                                             | Location | If the time is night, from 14000 to 22000 in-game time                                      |
| [NotInRegion](/skills/conditions/notinregion)                                 | Location | If the target location is not within the given WorldGuard region                            |
| [OffGCD](/skills/conditions/offgcd)                                           | Entity   | Checks if the target mob has an active Global Cooldown                                      |
| [OnBlock](/skills/conditions/onblock)                                         | Location | Matches the block the target entity is standing on                                          |
| [OnGround](/skills/conditions/onground)                                       | Entity   | If the target entity is standing on solid ground                                            |
| [Outside](/skills/conditions/outside)                                         | Location | If the target has open sky above them                                                       |
| [Owner](/skills/conditions/owner)                                             | Compare  | Checks if the target entity is the owner of the caster                                      |
| [OwnerIsOnline](/skills/conditions/ownerisonline)                             | Entity   | Checks if the owner of the target mob is online, if the owner is a player                   |
| [Pitch](/skills/conditions/pitch)                                             | Entity   | Checks if the pitch of the target entity is within a range                                  |
| [PlayerKills](/skills/conditions/playerkills)                                 | Entity   | Matches how many players the target mob has killed                                          |
| [PlayersInRadius](/skills/conditions/playersinradius)                         | Entity   | Checks how many players are in a radius                                                     |
| [PlayerNotWithin](/skills/conditions/playernotwithin)                         | Location | Checks if any players are within a radius of the target                                     |
| [PlayerWithin](/skills/conditions/playerwithin)                               | Location | Checks if any players are within a radius of the target                                     |
| [Raining](/skills/conditions/raining)                                         | Location | If it's raining in the target world                                                         |
| [Region](/skills/conditions/region)                                           | Location | If the target is within the given WorldGuard region                                         |
| [SameFaction](/skills/conditions/samefaction)                                 | Entity   | Tests if the caster and target are in the same faction                                      |
| [Score](/skills/conditions/score)                                             | Entity   | Checks a scoreboard value of the target entity                                              |
| [Mob Size](/skills/skills/conditions/mobsize)                                 | Entity   | Checks the size of the target entity                                                        |
| [PlayersOnline](/skills/conditions/playersonline)                             | Meta     | Matches the number of players online
| [Stance](/skills/conditions/stance)                                           | Entity   | Checks the stance of the target mob                                                         |
| [StringEquals](/skills/conditions/stringequals)                               | Meta     | Checks if value1 equals value2. Both values can use variables and placeholders.             |
| [Sunny](/skills/conditions/sunny)                                             | Location | If the weather is sunny in the target world.                                                |
| [TargetInLineOfSight](/skills/conditions/targetinlineofsight)                 | Entity   | Tests if the target has line of sight to their target                                       |
| [TargetNotInLineOfSight](/skills/conditions/targetnotinlineofsight)           | Entity   | Tests if the target doesn't have line of sight to their target                              |
| [TargetWithin](/skills/conditions/targetwithin)                               | Entity   | Tests if the target's target is within a certain distance                                   |
| [TargetNotWithin](/skills/conditions/targetnotwithin)                         | Entity   | Tests if the target's target is not within a certain distance                               |
| [Targets](/skills/conditions/targets)                                         | Meta     | Tests if the number of inherited targets from the parent skilltree matches the given range. |
| [Thundering](/skills/conditions/thundering)                                   | Location | If it's thundering in the target world                                                      |
| [VariableInRange](/skills/conditions/variableinrange)                         | Meta     | Checks if the given numeric variable is within a certain range.                             |
| [VariableIsSet](/skills/conditions/variableisset)                             | Meta     | Checks if the given variable is set.                                                        |
| [VariableEquals](/skills/conditions/variableequals)                           | Meta     | Checks if the given variable has a particular value.                                        |
| [Wearing](/skills/conditions/wearing)                                         | Entity   | Tests what the target entity has equipped.                                                  |
| [World](/skills/conditions/world)                                             | Location | Checks the name of the target world.                                                        |
| [WorldTime](/skills/conditions/worldtime)                                     | Location | Matches a range against the target location's world's time.                                 |
| [Yaw](/skills/conditions/yaw)                                                 | Entity   | Checks the yaw of the target entity against a range.                                        |
| [yDiff](/skills/conditions/ydiff)                                             | Entity   | Checks the difference in Y between the targeted entity and the caster.                      |

More Examples
-------------

    FlameShock:
      Cooldown: 1
      Conditions:
      - targetwithin 15
      - targetinlineofsight true
      - incombat
      - stance aggressive
      - onblock GRASS
      - offgcd
      Skills:
      - gcd{t=60}
      - message{m="<mob.name> begins casting a spell"}
      - potion{t=SLOW;d=60;l=7}
      - delay 60
      - message{m="<target.name> &ecombusts"}
      - effect:particles{p=flame;a=20;hS=3;vS=1;s=0;y=2}
      - potion{t=HARM;d=1;l=1}

[1] Not all conditions may be applicable everywhere.