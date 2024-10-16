## Description
Checks how many players are in a radius.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The given range value to check                                       | >0      |
| radius    | r, distance, d  | The given radius to check                                      | 32      |
| ignorespectator | is  | Whether players in spectator mode should be ignored                  | true    |


## Examples
```yaml
  Conditions:
  - playersinradius{a=>3;r=16}
```


## Aliases
- [x] pir
- [x] playerInRadius