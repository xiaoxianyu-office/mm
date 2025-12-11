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
You can find out more about these attributes by looking at [The Minecraft Wiki page regarding them](https://minecraft.wiki/w/Attribute#Attributes)

### AttackSpeed
Determines the recharge rate of a fully charged attack.
```yml
custom_item:
  Id: stick
  Attributes:
    MainHand:
      AttackSpeed: 0.1 MULTIPLY
```

### Armor
Sets the amount of armor.
1 armor is equal to 0.5 armor plates.
Vanilla caps the amount to 30.
```yml
custom_item:
  Id: diamond_chestplate
  Attributes:
    Chest:
      Armor: 2
```

### ArmorToughness
Alters the damage reduction percentage of the armor attribute. [MC wiki](https://minecraft.wiki/Armor#Armor_toughness).
```yml
custom_item:
  Id: diamond_chestplate
  Attributes:
    Chest:
      ArmorToughness: 0.5
```

### Damage
Sets the damage dealt by melee attacks.
1 damage equals to 0.5 hearts of damage dealt (without armor).
```yml
custom_item:
  Id: stick
  Attributes:
    All:
      Damage: 0.2 ADD_SCALAR
```

### Health
The maximum health modifier the user can have when either holding or wearing the item.
1 health equals to 0.5 hearts.
```yml
custom_item:
  Id: diamond_chestplate
  Attributes:
    MainHand:
      Health: 2 ADD
```

### Luck
Sets the amount of luck modifier of the item. 
This modifier affects the result of loot tables and also the [mob drops](/drops/Drops).
```yml
custom_item:
  Id: stick
  Attributes:
    OffHand:
      Luck: -10 ADD
```

### KnockbackResistance
Sets the horizontal scale knockback resisted from attacks.
```yml
custom_item:
  Id: diamond_chestplate
  Attributes:
    Chest:
      KnockbackResistance: 2 MULTIPLY_BASE
```

### MovementSpeed
Sets the movement speed modifier of the item.
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      MovementSpeed: -0.2 MULTIPLY_BASE
```

### MaxAbsorption
The maximum absorption of this mob.  
Determines the highest health they may gain by the Absorption effect
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      MaxAbsorption: 1 ADD
```

### Scale
The multiplier of the size of an entity
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      Scale: 2 ADD
```

### StepHeight‌
The maximum number of blocks that an entity can step up without jumping. Sneaking only prevents drops from heights that are higher than this attribute.[5] This only happens if the height that the player is above a block is equal or less than the attribute  
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      StepHeight: 2 ADD
```

### JumpHeight
The height an entity can jump, similar to the Jump Boost effect
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      JumpHeight: 2 ADD
```

### BlockInteractionRange
The block interaction range for players in blocks
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      BlockInteractionRange: 2 ADD
```

### EntityInteractionRange
The entity interaction range for players in blocks
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      EntityInteractionRange: 2 ADD
```

### BlockBreakSpeed
The speed the player can break blocks as a multiplier
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      BlockBreakSpeed: 2 ADD
```

### Gravity
The gravity affecting an entity in blocks per tick squared
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      Gravity: 2 ADD
```

### SafeFallDistance
The number of blocks an entity can fall before fall damage starts to be accumulated. Also the minimum amount of blocks the entity has to fall to make fallling particles and sounds
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      SafeFallDistance: 2 ADD
```

### FallDamageMultiplier‌
The amount of fall damage an entity takes as a multiplier
```yml
custom_item:
  Id: wooden_sword
  Attributes:
    All:
      FallDamageMultiplier‌: 2 ADD
```

## Examples
This example item will grant +10 luck when the item is held in the main
hand, but will grant +7 luck and +2 extra damage if the item is held in
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