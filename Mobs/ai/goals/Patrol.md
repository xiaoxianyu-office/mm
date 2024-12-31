## Description
Makes the mob follow a specific route, back and forth, multiple times


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| points    | p         | The points of the route, in a x1,y1,z1;x2,y2,z2;x3,y3,z3; syntax     |         |
| speed     | s         | The speed of the movement                                            | 1       |
| tolerance | t         | The minimum distance the mob must be from a point before moving to the next one| 3 |


## Examples
```yaml
  AIGoalSelectors:
  - clear
  - patrol{p=1,0,0;12,0,10}
```


## Aliases
- [x] patrolroute