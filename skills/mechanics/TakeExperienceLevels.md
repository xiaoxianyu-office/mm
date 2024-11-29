## Description
Takes experience levels to the targeted players


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of levels to take                                         | 0       |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  Skills:
  - takeexperiencelevels{a=1} @trigger ~onDamaged
```


## Aliases
- [x] takeexplevels


<!--TAGS-->
<!--tag:Experience-->

