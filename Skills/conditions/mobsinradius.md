## Description
Checks how many mobs are in a given radius


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| types     | type, t   | The types of mobs to check for                                       |         |
| amount    | a         | The range of mobs to check for                                       |         |
| radius    | r         | The radius to check                                                  |         |


## Examples
```yaml
  Conditions:
  - mobsInRadius{types=NewZombie;amount=5to10;radius=15}
```