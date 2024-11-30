## Description
Creates a particle orbital effect, where the particle will orbit around the targeted entity or location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius at which the particle orbits                              | 4       |
| points    | p         | How many points make up the circle                                   | 20      |
| ticks     | t         | For how many ticks this effect will last                             | 100     |
| interval  | in, i     | Tick speed at which the particle moves (faster tick rate=slower movement) | 10 |
| rotationX | rotX, rX  | Rotates the orbit around the X axis                                  | 0       |
| rotationY | rotY, rY  | Rotates the orbit around the Y axis                                  | 0       |
| rotationZ | rotZ, rZ  | Rotates the orbit around the Z axis                                  | 0       |
| offsetX   | offx, ox  | The X offset of the orbit's center                                   | 0       |
| offsetY   | offy, oy  | The Y offset of the orbit's center                                   | 0       |
| offsetZ   | offz, oz  | The Z offset of the orbit's center                                   | 0       |
| angularVelocityX | avx, vx | Modifies the angular velocity around the X axis                 | 0       |
| angularVelocityY | avy, vy | Modifies the angular velocity around the Y axis                 | 0       |
| angularVelocityZ | avz, vz | Modifies the angular velocity around the Z axis                 | 0       |
| rotate    |           | Whether the particles should rotate. Defaults to true if one of the angularvelocity attributes is greater than 0                                                   |         |
| reversed  | reverse   | Whether the particles should orbit in the opposite direction         | false   |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic


## Examples
```yaml
OrbitalParticleSkill:
  Skills:
  - particleorbital{r=2;points=16;t=100;i=1;vy=20;particle=flame} @self ~onSpawn
```


## Aliases
- [x] effect:particleorbital
- [x] e:particleorbital
- [x] effect:particlecircle
- [x] particlecircle
- [x] e:particlecricle


<!--TAGS-->
<!--tag:Effect:Particle-->
