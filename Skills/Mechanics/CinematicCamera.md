## Description
Plays a smooth cinematic camera path for the target player, moving their view along a series of keyframes. Useful for cutscenes, boss intros, and scripted reveals.

The path can be loaded from a file in the `cutscenes/` folder via the `path` attribute, or defined directly on the mechanic line with the `points` attribute. The mechanic must target a player. While a cinematic is playing you can query its state with the [cinematic placeholders](#placeholders) and the [isInCinematic](/Skills/Conditions/IsInCinematic) condition, and react to it with the [onCinematicStart](/Skills/Triggers/onCinematicStart) / [onCinematicEnd](/Skills/Triggers/onCinematicEnd) triggers.

[[_TOC_]]


## Attributes
| Attribute    | Aliases             | Description                                                                                  | Default           |
|--------------|---------------------|---------------------------------------------------------------------------------------------|-------------------|
| path         | p, name             | Name of a camera path defined under `cutscenes/`. Required if `points` is not set.           |                   |
| points       | keyframes           | Inline keyframes, semicolon-separated. Alternative to `path`. See [Keyframes](#keyframes).   |                   |
| duration     | d                   | Total duration in ticks. Used as the target length when keyframes have no per-leg `hold`.    | 100               |
| easing       | e, curve            | Default [easing curve](#easing-curves) for legs that do not override it.                      | EASE_IN_OUT_CUBIC |
| loop         |                     | Whether the path repeats until cancelled.                                                    | false             |
| maxDuration  | max, maxd           | Safety cap in ticks for looping paths, so a loop can never run forever.                       | 6000              |
| freezePlayer | freeze              | Makes the player invulnerable and locks their movement (walk/fly speed 0) for the duration.   | true              |
| mode         | m                   | `DISPLAY` (smooth, packet-only camera entity) or `TELEPORT` (per-tick teleport, no interpolation). | DISPLAY      |
| onStart      | onStartSkill, os    | Skill executed when the cinematic begins, with the player as caster.                          |<!--type:Metaskill-->|
| onEnd        | onEndSkill, oe      | Skill executed when the cinematic ends, with the player as caster.                            |<!--type:Metaskill-->|


### Path Files
Camera paths are YAML files placed in `plugins/MythicMobs/cutscenes/`. They are also discovered inside packs at `plugins/MythicMobs/packs/<PackName>/cutscenes/`. The file name does not matter; paths are referenced by their top-level id.

```yaml
my_path_id:
  duration: 100              # total ticks
  loop: false               # repeat until cancelled
  easing: EASE_IN_OUT_CUBIC # default leg easing
  points:
    - "world,x,y,z,yaw,pitch[,hold[,easing]]"
    - "~,dx,dy,dz,yaw,pitch[,hold[,easing]]"   # ~ = relative to the anchor
```

A path can then be played with `cinematicCamera{path=my_path_id} @target`.


### Keyframes
Each keyframe is `world,x,y,z,yaw,pitch`, with two optional trailing fields: `hold` and `easing`.

- **Absolute** points start with any loaded world name: `world,100,70,100,90,10`
- **Relative** points start with `~`, and treat `x/y/z` as offsets from the cinematic's **anchor**: `~,0,5,-10,0,30`. The anchor is the skill's origin (the [@origin](/Skills/Targeters/Origin)), which is normally the caster's location. Relative paths let one cutscene be reused anywhere.
- **`hold`** is the leg duration in ticks *from this point to the next*. When per-point holds are present they take priority; otherwise the path-level `duration` is split across the legs.
- **`easing`** on a point overrides the path-level easing for the leg leaving that point. For example a single `STEP` leg can cut sharply through an otherwise `CATMULL_ROM` path.

When using the inline `points` attribute, separate keyframes with `;`:
```yaml
points=world,100,70,100,90,10,40;~,0,3,-8,90,10,40,LINEAR
```


### Easing Curves
The `easing` attribute (and per-point easing) accepts any of the following:

`LINEAR`, `EASE_IN_QUAD`, `EASE_OUT_QUAD`, `EASE_IN_OUT_QUAD`, `EASE_IN_CUBIC`, `EASE_OUT_CUBIC`, `EASE_IN_OUT_CUBIC`, `EASE_IN_SINE`, `EASE_OUT_SINE`, `EASE_IN_OUT_SINE`, `SMOOTHSTEP`, `SMOOTHERSTEP`, `CATMULL_ROM`, `STEP`

`STEP` performs an instant jump cut. An unrecognised value falls back to `EASE_IN_OUT_CUBIC`.


### Mode
- **DISPLAY** (default) spawns a packet-only camera entity and spectates it, producing smooth interpolated motion.
- **TELEPORT** teleports the player every tick instead. It has no interpolation between ticks but is a reliable fallback.


## Placeholders
These [entity-scoped placeholders](/Skills/Placeholders) report the cinematic state of any player. Prefix them with a scope such as `caster.` or `target.`:

| Placeholder                     | Description                                                  |
|---------------------------------|-------------------------------------------------------------|
| `<caster.cinematic.active>`     | `true` / `false` — whether the player is in a cinematic     |
| `<caster.cinematic.frame>`      | Current frame, or `-1` if the player is not in a cinematic  |
| `<caster.cinematic.progress>`   | Progress from `0.0` to `1.0`, or `0` if not in a cinematic  |


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


## Building Paths In-Game
Camera paths can be authored without leaving the game using the `/mm camera` command, which captures your current position, yaw, and pitch as keyframes. See [Commands and Permissions](/Commands-and-Permissions#camera-commands) for the full syntax.


## Aliases

- [x] cinecam
- [x] camerapath
