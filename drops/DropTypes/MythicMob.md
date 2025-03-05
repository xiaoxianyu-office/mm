## Description
When dropped, some specified MythicMobs are spawned  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t, mob, m| The type of mob to summon. Can be a Mythic Mob type or a regular entity type                                                                 | SKELETON<!--type:Mob-->|
| amount    | a         | The number of mobs to summon.                                        | 1       |
| level     | lvl, l    | The level of the mob being summoned                                  | 0       |
| radius    | r, noise, n| The radius around the target within which the mobs will be summoned | 0       |
| yRadius   | yr, ynoise, yn| Overrides the Y component of radius.                             | radius  |
| yRadiusUpOnly | yradiusonlyup, yruo, yu| Whether the Y spread should only go upward, not downward.                                                                                      | false   |
| velocity | v, force, f| The maximum initial velocity the mob will have once summoned, making the mob be propelled in a random direction                                                                | 0       |
| yvelocity| yv, yforce, yf | Same as velocity, but only applied to the y axis                 | velocity|
| onSurface | os, s     |(true/false) Whether the mobs should be spawned only on a solid block | false   |


## Examples
```yaml
  Drops:
  - mythicmob{type=IncredibleLootchest;velocity=1;os=true} 1 1
```


## Aliases
- [x] mythicmobs
- [x] mm