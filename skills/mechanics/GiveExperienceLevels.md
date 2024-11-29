## Description
Gives experience levels to the targeted players


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of levels to give                                         | 0       |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  Skills:
  - giveexperiencelevels{a=1} @trigger ~onDamaged
```


## Aliases
- [x] giveexplevels


<!--TAGS-->
<!--tag:Experience-->