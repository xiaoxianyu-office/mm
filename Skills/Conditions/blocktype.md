## Description
This condition tests if material type present at the target location is the specified one.  
Valid for any [Spigot material type](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html), wildcards and block tags.


## Attributes
| Attribute | Aliases                   | Description                                          | Default |
|-----------|---------------------------|------------------------------------------------------|---------|
| types     | type, t, material, mat, m, block, b | A list of materials or MMOItem's block name to check. Does also support wildcards and block tags | DIRT<!--type:Block--><!--list--> |


## Examples
```yaml
  Conditions:
  - blocktype{type=dirt} true
```

```yaml
  Conditions:
  - blockType{type=#leaves,*_log,redstone_torch[lit=true]}
```

## Aliases
- [x] inblock
- [x] insideblock