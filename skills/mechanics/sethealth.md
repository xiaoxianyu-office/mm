## Description
Sets the health of the target entity.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | Amount of health to set to                                           | 1.0     |


## Examples
This example will set the players' health to 6 (3 hearts) when they
right-click the mob.
```yaml
  Skills:
  - sethealth{a=6} @trigger ~onInteract
  - ...
```


## Aliases
- [x] sethp


<!--TAGS-->
<!--tag:Health-->
