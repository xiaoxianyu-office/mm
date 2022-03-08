Goal: meleeAttack
--------------

Causes the mob to move to and melee attack its target

### Attributes

| Attribute | Aliases | Description             | Default |
|-----------|---------|-------------------------|:-------:|
| speed     | s       | Movement speed modifier |    1    |




### Examples

```yaml
ExampleMob:
  Type: Skeleton
  AIGoalSelectors:
    - clear
    - meleeattack{speed=1}
```