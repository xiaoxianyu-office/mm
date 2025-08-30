## Description
Checks against the material type that triggered the skill. Only works with specific [Triggers].


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| types     | type, t, material, mat, m, block, b | A list of [materials] to check against               | DIRT<!--type:Block--> |


## Examples
```yaml
  Conditions:
  - triggerblocktype{mat=STONE,DIRT} true
```


## Aliases
- [x] triggeringBlockType


<!-- LINKS -->
[materials]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html
[triggers]: /Skills/Triggers