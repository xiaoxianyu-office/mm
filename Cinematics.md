The cinematic camera system plays smooth, scripted camera paths for a specific player — useful for cutscenes, boss intros, and scripted reveals. A path is a series of keyframes (position + yaw + pitch) that the player's view is interpolated along.

Paths are played with the [cinematicCamera](/Skills/Mechanics/CinematicCamera) mechanic, either from a file in the `cutscenes/` folder or from inline keyframes. While a cinematic is playing you can query its state with the [cinematic placeholders](#placeholders) and the [isInCinematic](/Skills/Conditions/IsInCinematic) condition, and react to it with the [onCinematicStart](/Skills/Triggers/onCinematicStart) / [onCinematicEnd](/Skills/Triggers/onCinematicEnd) triggers.

[[_TOC_]]


## Path Files
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

| Key      | Description                                                          | Default           |
|----------|---------------------------------------------------------------------|-------------------|
| duration | Total length of the path in ticks, used when points have no `hold`. | 100               |
| loop     | Whether the path repeats until cancelled.                           | false             |
| easing   | Default [easing curve](#easing-curves) for legs that do not override it. | EASE_IN_OUT_CUBIC |
| points   | The list of [keyframes](#keyframes).                                |                   |


## Keyframes
Each keyframe is `world,x,y,z,yaw,pitch`, with two optional trailing fields: `hold` and `easing`.

- **Absolute** points start with any loaded world name: `world,100,70,100,90,10`
- **Relative** points start with `~`, and treat `x/y/z` as offsets from the cinematic's **anchor**: `~,0,5,-10,0,30`. The anchor is the skill's origin (the [@origin](/Skills/Targeters/Origin)), which is normally the caster's location. Relative paths let one cutscene be reused anywhere.
- **`hold`** is the leg duration in ticks *from this point to the next*. When per-point holds are present they take priority; otherwise the path-level `duration` is split across the legs.
- **`easing`** on a point overrides the path-level easing for the leg leaving that point. For example a single `STEP` leg can cut sharply through an otherwise `CATMULL_ROM` path.

When using the inline `points` attribute on the mechanic, separate keyframes with `;`:
```yaml
points=world,100,70,100,90,10,40;~,0,3,-8,90,10,40,LINEAR
```


## Easing Curves
The `easing` value (path-level, per-point, or the mechanic's `easing` attribute) accepts any of the following:

`LINEAR`, `EASE_IN_QUAD`, `EASE_OUT_QUAD`, `EASE_IN_OUT_QUAD`, `EASE_IN_CUBIC`, `EASE_OUT_CUBIC`, `EASE_IN_OUT_CUBIC`, `EASE_IN_SINE`, `EASE_OUT_SINE`, `EASE_IN_OUT_SINE`, `SMOOTHSTEP`, `SMOOTHERSTEP`, `CATMULL_ROM`, `STEP`

`STEP` performs an instant jump cut. An unrecognised value falls back to `EASE_IN_OUT_CUBIC`.


## Modes
- **DISPLAY** (default) spawns a packet-only camera entity and spectates it, producing smooth interpolated motion.
- **TELEPORT** teleports the player every tick instead. It has no interpolation between ticks but is a reliable fallback.


## Mechanics

### cinematicCamera
Plays a cinematic camera path for the target player. See the [cinematicCamera](/Skills/Mechanics/CinematicCamera) page for the full attribute list. The mechanic must target a player.

```yaml
  Skills:
  - cinematicCamera{path=intro_pan} @trigger
```

### cinematicCancel
Interrupts an active cinematic for the target player, immediately returning their camera and control. See the [cinematicCancel](/Skills/Mechanics/CinematicCancel) page.

```yaml
  Skills:
  - cinematicCancel @trigger
```


## Condition

### isInCinematic
Checks if the target player is currently in an active cinematic. See the [isInCinematic](/Skills/Conditions/IsInCinematic) page.


## Triggers
Both triggers fire with the player the cinematic is playing for as the caster.

- [onCinematicStart](/Skills/Triggers/onCinematicStart) — fires when a path begins playing on a player.
- [onCinematicEnd](/Skills/Triggers/onCinematicEnd) — fires when a path ends, however it ends (natural finish, [cinematicCancel](/Skills/Mechanics/CinematicCancel), player quit, or player death).


## Placeholders
These [entity-scoped placeholders](/Skills/Placeholders) report the cinematic state of any player. Prefix them with a scope such as `caster.` or `target.`:

| Placeholder                     | Description                                                  |
|---------------------------------|-------------------------------------------------------------|
| `<caster.cinematic.active>`     | `true` / `false` — whether the player is in a cinematic     |
| `<caster.cinematic.frame>`      | Current frame, or `-1` if the player is not in a cinematic  |
| `<caster.cinematic.progress>`   | Progress from `0.0` to `1.0`, or `0` if not in a cinematic  |


## Commands
Camera paths can be authored in-game with the `/mm camera` command, which captures your current position, yaw, and pitch as a keyframe. Requires the `mythicmobs.command.camera` permission. See [Commands and Permissions](/Commands-and-Permissions#camera-commands) for the full syntax.

- **/mm camera &lt;pathId&gt; add [index] [hold=N] [easing=NAME] [relative=true]** — adds a keyframe at your current location.
- **/mm camera &lt;pathId&gt; remove [index]** — removes the keyframe at the given index (the last one if omitted).


## Examples
A boss intro: freeze the triggering player, orbit the boss for 80 ticks, then run a skill when it ends.
```yaml
BossIntro:
  Skills:
  - cinematicCamera{path=boss_orbit;freezePlayer=true;onEnd=BossRoar} @trigger
```
