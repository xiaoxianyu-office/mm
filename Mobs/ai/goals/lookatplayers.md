## Description
Causes the mob to look at nearby players


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| range | radius,r        | The range to look for players                                              |    5    |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - lookatplayers{r=12}
```


## Aliases
- [x] lookatplayer