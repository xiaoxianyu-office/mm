## Description
Paths to an entity that checks some conditions


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed | s | The speed modifier | 1 |
| maxrange | range, r | The maximum range from the target entity | 32.0 |
| targetconditions | conditions, cond, c | The conditions the target entity must match | <!--type:Conditions--> |


## Examples
```yaml
  AIGoalSelectors:
  - clear
  - MoveTowardsTargetConditional{s=2;maxrange=6;targetConditions=[
    - isPlayer true
    ]}
```


## Aliases
- [x] moveTowardsTargetCond