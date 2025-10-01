## Description
Makes an armor stand assume a pose over a specified time


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| duration  | d         | The duration of the animation in ticks                               | 1       |
| smart     |           | Whether to apply smart angle conversion                              | true    |
| ignoreempty | ie      | Whether to ignore empty pose values                                  | true    |
| usedegrees  | ud      | Interprets the input' values as degrees (0-360) if set to true and as radians (0-6.28) if set to false                                                                       | true    |
| head      | h         | The pose for the armorstand's head                                   |         |
| body      | b         | The pose for the armorstand's body                                   |         |
| leftarm   | la        | The pose for the armorstand's left arm                               |         |
| rightarm  | ra        | The pose for the armorstand's right arm                              |         |
| leftleg   | ll        | The pose for the armorstand's left leg                               |         |
| rightleg  | rl        | The pose for the armorstand's right leg                              |         |

  

## Examples
```yaml
  Skills:
  - animatearmorstand{d=10;leftarm=90,0,0;rightarm=270,0,0;ignoreempty=false}
```


## Aliases
- [x] animateas
- [x] animas