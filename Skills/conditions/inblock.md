## Description
Checks the material at the target location. See the [Spigot Javadoc](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html) for a list of valid materials


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| block     | blocks, b, material, mat, m | A list of blocks to match                          |         |


## Examples
```yaml
  Conditions:
  - inblock{b=WATER,LAVA} false
```


## Aliases
- [x] insideblock