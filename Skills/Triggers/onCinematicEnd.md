## Description
Executes the skill when a [cinematicCamera](/Skills/Mechanics/CinematicCamera) path stops playing on a player.
> The caster of this trigger is the player the cinematic was playing for. There is no separate associated [@trigger](/Skills/Targeters/Trigger).

This fires no matter how the cinematic ended: when the path finishes naturally, when it is interrupted by [cinematicCancel](/Skills/Mechanics/CinematicCancel), when the player quits, or when the player dies. It is the reliable place to restore state (UI, effects, control) since it always runs once per cinematic. To run a skill only for one specific cinematic, prefer the mechanic's `onEnd` attribute instead.


## Examples
```yml
CinematicWatcher:
  Type: ARMOR_STAND
  Skills:
  # Restore the player's HUD whenever their cinematic ends, however it ends
  - setVariable{var=caster.hud;value=shown} @self ~onCinematicEnd
```
