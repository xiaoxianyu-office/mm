## Description
Creates a puff of smoke at the location of the targeter.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| direction | dir, d    | The direction the effect should play towards. Can be an integer from 1 to 4| 4 |


## Examples
```yaml
SmokeMonster:
  Type: ZOMBIE
  Skills:
  - smoke @target ~onTimer:10
  - smoke{direction=2} @self ~onAttack
```


## Aliases
- [x] effect:smoke
- [x] e:smoke


<!--TAGS-->
<!--tag:Effect-->
