## Description
Summons a falling block of the specified material at the targeted locations


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | types, t, material, mat, m | The [material] of the falling block                 | DIRT<!--type:Block--> |


## Examples
```yaml
  Skills:
  - summonfallingblock{m=ANVIL} @PlayerLocationsInRadius{r=20;y=10}
```


<!-- LINKS -->
[material]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html


<!--TAGS-->
<!--tag:Summon-->