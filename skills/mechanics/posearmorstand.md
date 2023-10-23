## Description
Moves the extremities of an armorstand, the value is in radians.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| head      |           |                                                                      | 0,0,0   |
| body      |           |                                                                      | 0,0,0   |
| leftarm   |           |                                                                      | 0,0,0   |
| rightarm  |           |                                                                      | 0,0,0   |
| leftleg   |           |                                                                      | 0,0,0   |
| rightleg  |           |                                                                      | 0,0,0   |

  
## Examples
```yaml
  Skills:
  - posearmorstand{head=0.78,0,0} @self ~onSpawn
  - ...
```