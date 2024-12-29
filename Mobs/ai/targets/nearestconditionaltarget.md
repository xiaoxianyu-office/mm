## Description
Causes the mob to target based on conditions.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| interval | int,i        | Determines the chance for the goal to be ran                       |    0    |
| mustsee | ms        | Whether the mob has to be able to see the target                       | true    |
| mustreach | mr        | Whether the mob has to be able to reach the target                   | false   |
| conditions | c, cond, targetconditions | The conditions to use                               |         |


## Examples
Would cause the mob to target entities holding Iron Ingots.
```yaml
ExampleMob:
  Type: ZOMBIE
  AITargetSelectors:
    - clear
    - nearestconditionaltarget{mr=true;ms=true;conditions=[ - holding{m=IRON_INGOT} true ]}
```


## Aliases
- [x] nearestconditional
- [x] nearestif