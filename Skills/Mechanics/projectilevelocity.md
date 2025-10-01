## Description

Modifies the velocity of the calling [Projectile](/skills/mechanics/projectile) or [Missile](/skills/mechanics/missile). In this context, it works the same as the [Velocity](/skills/mechanics/velocity) mechanic.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| mode      | m         | The operation to perform. Can be SET, ADD, REMOVE, DIVIDE, or MULTIPLY. | SET<!--type:Velocity_Mode-->|
| velocityx | vx, x     | Velocity on the x-axis. Can be negative.                             | 1       |
| velocityy | vy, y     | Velocity on the y-axis. Can be negative.                             | 1       |
| velocityz | vz, z     | Velocity on the z-axis. Can be negative.                             | 1       |
| relative  | r         | If the change in velocity should be relative to the projectile's facing direction. In this instance, the `z` axis becomes `forward/backward`, `y` becomes `up/down` and `x` becomes `left/right`| true     |


## Examples
```yaml
Projectile-onTick:
  Conditions:
  - chance{chance=0.1} true
  Skills:
  - projectilevelocity{mode=ADD;vz=0.3}
```


## Aliases
- [x] pvelocity


<!--TAGS-->
<!--tag:Meta-->

