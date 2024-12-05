## Description
Checks against the material of the item that triggered the skill.  
Wildcards (`*_SWORD`) and item tags (`#arrows`)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| types     | type, t, material, mat, m | A list of [materials] to check against               | DIRT    |


## Examples
```yaml
  Conditions:
  - itemType{types=STONE,STONE_SWORD} true
```


<!-- LINKS -->
[materials]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html