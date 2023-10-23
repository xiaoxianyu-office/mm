## Description
Sets the targeted entity on fire.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| ticks     | t,d,duration | How many ticks the target should burn                             | 60      |


## Examples
Ignites the entity that the mob using this skill is attacking for 100
ticks (5 seconds)
```yaml
  Skills:
  - ignite{ticks=100} @trigger ~onAttack
```