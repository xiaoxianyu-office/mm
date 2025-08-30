## Description
Checks if the target entity's equipped item has an enchantment. A list of valid enchantments can be found in the [Spigot Javadoc](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
|enchantment|type, ench, e, t| The enchantment to test for                                     | ANY     |
| level     | lvl, l    | The level to test for                                                | >0      |


## Examples:
```yaml
  TargetConditions:
  - hasenchantment{e=DAMAGE_ALL;l=>3} true
```


## Aliases
- [x] hasEnchant