## Description
Sets the gamemode of the target player. Does nothing if the target is
not a player. Requires the `sync=true` attribute.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| mode      | m         | The gamemode to change the target to.                                | SURVIVAL<!--type:Gamemode-->|


## Examples
```yaml
  Skills:
  - setgamemode{m=CREATIVE;sync=true} @PlayersInRadius{r=10} ~onSpawn
  - ...
```