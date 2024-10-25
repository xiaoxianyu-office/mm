The enchantments attribute is used to apply enchantments to items made using MythicMobs.
Any of these can be put on any item and can exceed natural enchantment-level limits set by Minecraft.
Some enchantments may not have any effects if put on items that they weren't made for.

Syntax
------
```yml
internal_itemname:
  Id: <material>
  Enchantments:
  - <enchantment> <level>
  - <enchantment> <level>
  - ...
```
**\<enchantment>**  
Type of enchantment to be applied to the specified item.

**\<level>**  
The level of the specified enchantment.

## Available Enchantments

A list of available [enchantments](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html) can be found on spigot javadocs

Enchantments can also be added via the `namespace:enchant_name` syntax, if there are other providers

## Example
```yml
lethal_pickaxe:
  Id: diamond_pickaxe
  Enchantments:
  - SHARPNESS 3
  - KNOCKBACK 1
  - mythic:example_enchant 2
```