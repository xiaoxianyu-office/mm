## Description
Changes the target color, can only be applied to colorable mobs such as
shulkers or sheeps.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| color     | c         | The color name                                                       |<!--type:DyeColor-->|


## Examples
Sets the color of colorable mobs to blue when it spawns.
```yaml
  Skills:
  - setcolor{color=blue} @self ~onSpawn
  - ...
```


## Aliases
- [x] setcolor