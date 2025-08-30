## Description
Checks against the item material type that triggered the skill. Only works with specific [Triggers].


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| types     | type, t, material, mat, m, items, item, i | A list of [materials] to check against | DIRT<!--type:Material--><!--list--> |


## Examples
```yaml
  Conditions:
  - triggeritemtype{mat=STONE,DIRT,STONE_SWORD} true
```


## Aliases
- [x] triggeringItemType


<!-- LINKS -->
[materials]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html
[triggers]: /Skills/Triggers