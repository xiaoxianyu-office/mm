## Description
Interrupts an active [cinematicCamera](/Skills/Mechanics/CinematicCamera) for the target player, immediately returning their camera and control. The mechanic must target a player.

Cancelling fires the [onCinematicEnd](/Skills/Triggers/onCinematicEnd) trigger (and the original mechanic's `onEnd` skill) with an end reason of `CANCELLED`. If the target player is not currently in a cinematic, the mechanic does nothing.


## Attributes
*This mechanic has no attributes*


## Examples
Cancels the cinematic playing for the triggering player.
```yaml
  Skills:
  - cinematicCancel @trigger
```
##
Ends any cinematic for the player if they take damage during it.
```yaml
  Skills:
  - cinematicCancel{} @self ~onDamaged
```


## Aliases

- [x] cinecancel
- [x] stopcinematic
