## Description
Executes the skill when a [cinematicCamera](/Skills/Mechanics/CinematicCamera) path begins playing on a player.
> The caster of this trigger is the player the cinematic is playing for. There is no separate associated [@trigger](/Skills/Targeters/Trigger).

This trigger fires for every cinematic start, regardless of whether the path was started from a named file or from inline keyframes. To run a skill only for one specific cinematic, prefer the mechanic's `onStart` attribute instead.


## Examples
```yml
CinematicWatcher:
  Type: ARMOR_STAND
  Skills:
  # Hide the player's bossbar UI the moment any cinematic starts
  - setVariable{var=caster.hud;value=hidden} @self ~onCinematicStart
```
