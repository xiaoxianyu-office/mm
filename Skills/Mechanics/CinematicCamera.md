## Description
Plays a smooth cinematic camera path for the target player, moving their view along a series of keyframes. Useful for cutscenes, boss intros, and scripted reveals. The mechanic must target a player.

The path can be loaded from a file in the `cutscenes/` folder via the `path` attribute, or defined directly on the mechanic line with the `points` attribute. See the [Cinematics](/Cinematics) page for the path-file format, [keyframes](/Cinematics#keyframes), [easing curves](/Cinematics#easing-curves), [modes](/Cinematics#modes), placeholders, and the in-game authoring command.


## Attributes
| Attribute    | Aliases             | Description                                                                                  | Default           |
|--------------|---------------------|---------------------------------------------------------------------------------------------|-------------------|
| path         | p, name             | Name of a camera path defined under `cutscenes/`. Required if `points` is not set.           |                   |
| points       | keyframes           | Inline [keyframes](/Cinematics#keyframes), semicolon-separated. Alternative to `path`.        |                   |
| duration     | d                   | Total duration in ticks. Used as the target length when keyframes have no per-leg `hold`.    | 100               |
| easing       | e, curve            | Default [easing curve](/Cinematics#easing-curves) for legs that do not override it.          | EASE_IN_OUT_CUBIC |
| loop         |                     | Whether the path repeats until cancelled.                                                    | false             |
| maxDuration  | max, maxd           | Safety cap in ticks for looping paths, so a loop can never run forever.                       | 6000              |
| freezePlayer | freeze              | Makes the player invulnerable and locks their movement (walk/fly speed 0) for the duration.   | true              |
| mode         | m                   | [`DISPLAY`](/Cinematics#modes) (smooth) or `TELEPORT` (per-tick teleport, no interpolation).  | DISPLAY           |
| onStart      | onStartSkill, os    | Skill executed when the cinematic begins, with the player as caster.                          |<!--type:Metaskill-->|
| onEnd        | onEndSkill, oe      | Skill executed when the cinematic ends, with the player as caster.                            |<!--type:Metaskill-->|


## Examples
Plays a named path from `cutscenes/` for the triggering player.
```yaml
  Skills:
  - cinematicCamera{path=intro_pan} @trigger
```
##
Defines the whole path inline with two keyframes and a custom easing, lasting 80 ticks.
```yaml
  Skills:
  - cinematicCamera{points=world,100,70,100,90,10,40;world,120,72,100,90,10,40,LINEAR;easing=CATMULL_ROM;duration=80} @trigger
```
##
Plays a looping orbit around the boss, capped at 60 seconds, and restores the player's HUD when it ends.
```yaml
  Skills:
  - cinematicCamera{path=boss_orbit;loop=true;maxDuration=1200;onEnd=RestoreHud} @target
```


## Aliases

- [x] cinecam
- [x] camerapath
