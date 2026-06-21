## Description
Shoots a volley of arrows or item-projectiles at the targeted entity or
location that deals damage. Can use any attribute from the Shoot
mechanic.


## Attributes
| Attribute | Aliases   | Description                                                                 | Default |
|-----------|-----------|-----------------------------------------------------------------------------|---------|
| amount    | a         | The amount of projectiles                                                   | 10      |
| source    | s         | The type of the volley. Can be REGULAR or RAIN                              | REGULAR<!--type:REGULAR,RAIN-->|
| radius    | r         | The radius of the volley spread. **Only applies when `source=RAIN`.**       | 0       |
| yoffset   | y         | The vertical offset of the rain source above the target. **Only applies when `source=RAIN`.** | 1       |
| spread    | sp        | How spread out the volley is (random yaw/pitch jitter, in degrees)          | 0       |
| canPickup | pickup    | Whether the arrows can be picked up by players                              | true    |
> This mechanic inherits every *inheritable* attribute of the [Shoot](/Skills/Mechanics/Shoot) mechanic

> **Adjusting the origin of a REGULAR volley:** `radius` and `yoffset` are only used by `source=RAIN`.
> To shift where a `REGULAR` volley spawns from (e.g. to stop arrows clipping into the ground under the mob),
> use the inherited Shoot attributes `startyoffset` (`syo`), `forwardoffset` (`sfo`), and `startsideoffset` (`sso`).


## Examples
```yaml
  Skills:
  - volley{type=EGG;velocity=5;damage=10;amount=20}
  # Raise a REGULAR volley so arrows don't spawn in the block below the caster
  - volley{amount=10;spread=5;startyoffset=1.5}
  # A rain of arrows falling in a 4-block radius, 20 blocks above the target
  - volley{source=RAIN;amount=30;radius=4;yoffset=20}
```


## Aliases
- [x] shootvolley


<!--TAGS-->
<!--tag:Projectile-->
<!--tag:Meta-Mechanic-->
