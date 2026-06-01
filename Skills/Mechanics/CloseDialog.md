## Description
Closes any open [Dialog](/Dialogs) for the target player.

This is the counterpart to the [showDialog](/Skills/Mechanics/ShowDialog) mechanic. If the target player has no dialog open, the mechanic does nothing. When used without a targeter, it affects the caster.

> **This is a [Paper-Only] mechanic!**

> **This is a [Premium-Only] mechanic!**


## Attributes
*This mechanic has no attributes*


## Examples
Closes the dialog for the player that interacted with the mob.
```yaml
  Skills:
  - closeDialog @trigger
```
##
Closes the dialog for all players within 10 blocks.
```yaml
  Skills:
  - closeDialog @PlayersInRadius{r=10}
```


## Aliases

- [x] hideDialog


<!-- LINKS -->
[Paper-Only]: https://papermc.io/downloads/all
[Premium-Only]: Premium-Features
