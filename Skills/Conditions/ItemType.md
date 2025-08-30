## Description
Checks against the material of the item that triggered the skill.  
Uses the [Item Matcher](/Items/Item-Matcher)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| types     | type, t, material, mat, m, i, item | A list of [materials] to check against               | DIRT<!--type:Item--><!--list-->|
| strict    | exact, e  | Whether the matcher should more strictly match the target item       | false   |
| vanillaonly | vanilla | Whether the matched item can only be a vanilla one                   | false   |


## Examples
```yaml
  Conditions:
  - itemType{types=STONE,STONE_SWORD} true
```


<!-- LINKS -->
[materials]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html


<!--TAGS-->
<!--tag:ItemMatcher-->