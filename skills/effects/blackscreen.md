## Description
Causes the player's screen to black out.  

> This creates an aura called `#blackScreen`, with an `interval` of 10, a maximum of 1 `stack` and the ability to refresh its original if an aura of the same name is applied again


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| duration  | d         | The duration of the effect                                           |         |
| cancel    | c         | Whether the effect should be cancelled instead                       |


## Examples
Blinds players when the mob teleports
```yaml
BlackScreen:
  Skills:
  - blackscreen{d=2} @PlayersInRadius{r=100} ~onTeleport
```


## Aliases
- [x] effect:blackScreen
- [x] e:blackScreen