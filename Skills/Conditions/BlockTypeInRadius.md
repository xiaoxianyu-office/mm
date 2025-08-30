## Description
Checks against the amount of specified blocks in a radius around the evaluated location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| types     | type, t, material, mat, m, b, block | A list of [materials] to check against               | DIRT<!--type:Block--><!--list--> |
| radius    | r         | The radius                                                           | 8       |
| amount    | a         | The amount of blocks to match                                        | >0      |


## Examples
```yaml
  TargetConditions:
  - blockTypeInRadius{type=STONE;amount=>10;radius=3} true
```


<!-- LINKS -->
[materials]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html