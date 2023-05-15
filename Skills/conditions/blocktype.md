## Description
This condition tests if material type present at the target location is the specified one.  
Valid for any [Bukkit material type](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html).


## Attributes

| Attribute | Aliases                   | Description                                          | Default |
|-----------|---------------------------|------------------------------------------------------|---------|
| types     | type, t, material, mat, m | A list of materials or MMOItem's block name to check | DIRT    |


## Examples

```yaml
Conditions:
- blocktype{type=dirt} true
```