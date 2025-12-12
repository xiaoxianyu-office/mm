The attributes section for items made with MythicMobs handles the Minecraft attribute system.
It makes it possible to apply different attributes given to the entity wearing/using the item depending on the slot.

[[_TOC_]]

## Format
```yml
Item:
  Id: item_id
  Attributes:
    [Slot]:
      [Attribute]: [value] <operation> 
```


## Slots
| Slot     | Description                                                               |
|----------|---------------------------------------------------------------------------|
| All      | Will apply the given attributes to all slots.                             |
| MainHand | Attributes will only apply if item is being held in the main hand.        |
| OffHand  | Attributes will only apply if item is being held in the off hand.         |
| Head     | Attributes will only apply if item is being worn on the head slot.        |
| Chest    | Attributes will only apply if item is being worn on the chest/torso slot. |
| Legs     | Attributes will only apply if item is being worn on the legs slot.        |
| Feet     | Attributes will only apply if item is being worn on the feet slot.        |


## Value
You can input both absolute or relative values:
- To input an absolute value, simply write it out
```yaml
      Damage: 10 ADD
```
- To input a relative value, use a % symbol after it
```yaml
      Damage: 10% ADD
```


## Operations
| Operation     | Aliases            | Description                                                                                       |
|---------------|--------------------|---------------------------------------------------------------------------------------------------|
| ADD           | 0, ADD_NUMBER      | Adds or subtracts the specified value to the base value.                                          |
| MULTIPLY_BASE | 1, ADD_SCALAR      | Multiplies the base value with the sum of all the modifier's amount.                              |
| MULTIPLY      | 2, MULTIPLY_SCALAR | Similar to `MULTIPLY_BASE` but multiplies all the modifier's amount instead of adding all of them |

[*See MC wiki on how the game calculates the value for all modifiers*](https://minecraft.wiki/w/Attribute#Modifiers)


## Attributes
These are all the available attributes that can be put on the item.
You can use general placeholders like `<random.#to#>` or `<random.float.#to#>`.  
Most of the explanations on this page are excerpts from the [Minecraft Wiki](https://minecraft.wiki). You can find out more information about these attributes by looking at [Their page regarding them](https://minecraft.wiki/w/Attribute#Attributes)

<!-- ENUM mythicbukkitattributes START -->

### ATTACK_DAMAGE
Sets the damage dealt by melee attacks.
1 damage equals to 0.5 hearts of damage dealt (without armor).
```yml
custom_item:
  Id: stick
  Attributes:
    All:
      ATTACK_DAMAGE: 0.2 ADD_SCALAR
```

### ATTACK_SPEED
Determines recharging rate of attack strength. Its value is the number of full-strength attacks per second.
```yml
custom_item:
  Id: stick
  Attributes:
    MainHand:
      ATTACK_SPEED: 0.1 MULTIPLY
```

### MAX_HEALTH
The maximum health modifier the user can have when either holding or wearing the item.
1 health equals to 0.5 hearts.
```yml
custom_item:
  Id: diamond_chestplate
  Attributes:
    MainHand:
      MAX_HEALTH: 2 ADD
```

### MOVEMENT_SPEED
Movement speed is the speed at which entities can move, but this is not the actual speed value in blocks/second. The entity's actual speed in blocks/second is a bit over 20 times this value.
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      MOVEMENT_SPEED: -0.2 MULTIPLY_BASE
```

### FLYING_SPEED
This attribute is a flight speed modifier in some unknown metric
```yaml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      FLYING_SPEED: 1 ADD
```

### ATTACK_KNOCKBACK
Determines the knockback applied to attacks
```yaml
custom_item:
  Id: stick
  Attributes:
    MainHand:
      ATTACK_KNOCKBACK: 1 ADD
```

### KNOCKBACK_RESISTANCE
Determines the scale of horizontal knockback resisted from attacks and projectiles. Vertical knockback is not affected. It does not affect explosions.  
The resistance functions as a percentage from 0.0 (0% resistance) to 1.0 (100% resistance) (e.g. 0.4 is 40% resistance, meaning the attributed entity takes 60% of usual knockback)
```yml
custom_item:
  Id: diamond_chestplate
  Attributes:
    Chest:
      KNOCKBACK_RESISTANCE: 2 MULTIPLY_BASE
```

### ARMOR
This attribute defines the [armor defense points](https://minecraft.wiki/w/Armor#Armor_points).
1 armor is equal to 0.5 armor plates.  
Armor points above 20 will not be shown, and the actual cap is at 30.  
```yml
custom_item:
  Id: diamond_chestplate
  Attributes:
    Chest:
      ARMOR: 2
```

### ARMOR_TOUGHNESS
Alters the damage reduction percentage of the armor attribute. [MC wiki](https://minecraft.wiki/Armor#Armor_toughness).
```yml
custom_item:
  Id: diamond_chestplate
  Attributes:
    Chest:
      ARMOR_TOUGHNESS: 0.5
```

### LUCK
Sets the amount of luck modifier of the item. 
This modifier affects the [result of loot tables](https://minecraft.wiki/w/Attribute#Luck) and also the [mob drops](/drops/Drops).
```yml
custom_item:
  Id: stick
  Attributes:
    OffHand:
      LUCK: -10 ADD
```

### SCALE
The multiplier of the size of an entity
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      SCALE: 2 ADD
```

### FOLLOW_RANGE
This attribute determines the range in blocks within which a mob with this attribute targets players or other mobs to track. Exiting this range causes the mob to cease following the player/mob
```yaml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      FOLLOW_RANGE: 1 ADD
```

### FALL_DAMAGE_MULTIPLIER
The amount of fall damage an entity takes as a multiplier
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      FALL_DAMAGE_MULTIPLIER: 2 ADD
```

### SAFE_FALL_DISTANCE
The number of blocks an entity can fall before fall damage starts to be accumulated. Also the minimum amount of blocks the entity has to fall to make falling particles and sounds
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      SAFE_FALL_DISTANCE: 2 ADD
```

### GRAVITY
The gravity affecting an entity in blocks per tick squared
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      GRAVITY: 2 ADD
```

### BLOCK_BREAK_SPEED
The speed the player can break blocks as a multiplier
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      BLOCK_BREAK_SPEED: 2 ADD
```

### ENTITY_INTERACTION_RANGE
The entity interaction range for players in blocks
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      ENTITY_INTERACTION_RANGE: 2 ADD
```

### BLOCK_INTERACTION_RANGE
The block interaction range for players in blocks
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      BLOCK_INTERACTION_RANGE: 2 ADD
```

### JUMP_HEIGHT
This attribute determines the initial vertical velocity of an entity when they jump, in blocks per tick
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      JUMP_HEIGHT: 2 ADD
```

### STEP_HEIGHT
The maximum number of blocks that an entity can step up without jumping. Sneaking only prevents drops from heights that are higher than this attribute. This only happens if the height that the player is above a block is equal or less than the attribute  
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      STEP_HEIGHT: 2 ADD
```

### MAX_ABSORPTION
The maximum absorption of this entity.  
Determines the highest health they may gain by the Absorption effect
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      MAX_ABSORPTION: 1 ADD
```


### BURNING_TIME
This attribute is a multiplier for how long an entity should remain on fire after being ignited.  
A value of 0 eliminates the burn time.  
It has no impact on the burning time increase when staying in fire
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      BURNING_TIME: 1 ADD
```

### EXPLOSION_KNOCKBACK_RESISTANCE
This attribute defines what percentage of knockback from explosions an entity resists.  
A value of 1 eliminates the knockback
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      EXPLOSION_KNOCKBACK_RESISTANCE: 1 ADD
```

### MOVEMENT_EFFICIENCY
This attribute is a factor to improve walking on terrain that slows down movement.  
A value of 1 removes the slowdown
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      MOVEMENT_EFFICIENCY: 1 ADD
```

### OXYGEN
This attribute determines the chance that an entity's Air data tag decreases in any given game tick, while the entity is underwater. The chance is given by $`\frac{1}{(OXYGEN + 1)}`$
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      OXYGEN: 1 ADD
```

### SNEAKING_SPEED
This attribute determines the movement speed factor when sneaking or crawling.  
A factor of 1 means sneaking or crawling is as fast as walking, a factor of 0 means unable to move while sneaking or crawling.
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      SNEAKING_SPEED: 1 ADD
```

### WATER_MOVEMENT_EFFICIENCY
This attribute is a factor of movement speed when submerged. A higher value lets entities move faster. This represents only the submersion factor itself; other factors (such as sprinting) also apply.
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      WATER_MOVEMENT_EFFICIENCY: 1 ADD
```

### SUBMERGED_MINING_SPEED
This attribute determines the mining speed factor when underwater. A factor of 1 means mining as fast as on land, a factor of 0 means unable to mine while submerged. This represents only the submersion factor itself; other factors (such as not touching the ground) also apply.
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      SUBMERGED_MINING_SPEED: 1 ADD
```

### MINING_EFFICIENCY
This attribute is a factor to speed up the mining of blocks when using the right tool.
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      MINING_EFFICIENCY: 1 ADD
```

### TEMPT_RANGE
This attribute determines the range, in blocks, in which mobs can be tempted. When tempted, mobs follow the player while the player is holding a specific item.
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      TEMPT_RANGE: 1 ADD
```

### SWEEPING_DAMAGE_RATIO
This attribute determines how much of the base attack damage gets transferred to secondary targets in a sweep attack. This is in addition to the base attack of the sweep damage itself. A value of 1 means that all of the base attack damage is transferred (sweep damage is attack_damage + 1)
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      SWEEPING_DAMAGE_RATIO: 0.5 ADD
```

### SPAWN_REINFORCEMENTS
This attribute determines the chance for a zombie to spawn another zombie when attacked
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      SPAWN_REINFORCEMENTS: 0 MULTIPLY
```

<!-- ENUM mythicbukkitattributes STOP -->

## Examples
This example item will grant +10 luck when the item is held in the main hand, but will grant +7 luck and +2 extra damage if the item is held in
the offhand slot:
```yml
lucky_charms:
  Id: potato_item
  Display: 'Rotten Lucky Charm'
  Attributes:
    MainHand:
      Luck: 10
    OffHand:
      Luck: 7
      Damage: 2
```
This example item grants +2 extra health no matter which slot the item is being held, but will also grant +4% movement speed if the item is worn in the feet slot:
```yml
happy_feet:
  Id: leather_boots
  Display: 'Penguin Hide'
  Attributes:
    All:
      Health: 2
    Feet:
      MovementSpeed: 0.04
```
Each time this item is generated it will have a random damage value between 3 and 5 and a random speed bonus between 1% and 5% when worn in the main hand:
```yml
lucky_sword:
  Id: wood_sword
  Display: '<yellow>Lucky Sword</yellow>'
  Attributes:
    MainHand:
      Damage: 3-5
      MovementSpeed: 0.01-0.05 MULTIPLY_BASE
```