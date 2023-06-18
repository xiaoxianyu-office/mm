Effect: ParticleOrbital
----

Creates a particle orbital effect, where the particle will orbit around the targeted entity or location.

A list of particle types can be found [here](/skills/effects/particles/types).

### Attributes
----

#### Particle Attributes
Options for regular particles are applicable.

#### General Attributes

| Attribute  | Aliases | Description | Default Value |
| ------ | ------ | ------ | ------ |
| radius | r  | The radius at which the particle orbits  | 4 |
| points | p | How many points make up the circle | 20 |
| ticks | t | How many ticks this will last | 100 |
| interval | in,i  | Tick speed at which the particle moves (faster tick rate=slower movement) | 10     |
| rotationX | rotX,rX  | Rotates the orbit around the X axis | 0     |
| rotationY | rotY,rY  | Rotates the orbit around the Y axis | 0     |
| rotationZ | rotZ,rZ  | Rotates the orbit around the Z axis | 0     |
| offsetX | offx,ox   | The X offset of the orbit's center | 0 |
| offsetY | offy,oy   | The Y offset of the orbit's center | 0 |
| offsetZ | offz,oz   | The Z offset of the orbit's center | 0 |
| angularVelocityX | avx,vx  | Modifies the angular velocity around the X axis | 0   |
| angularVelocityY | avy,vy  | Modifies the angular velocity around the Y axis | 0   |
| angularVelocityZ | avz,vz  | Modifies the angular velocity around the Z axis | 0   |
| reversed | reverse | Makes the particles orbit backwards | false |

Example
-------

    - effect:particleorbital{r=2;points=16;t=100;i=1;vy=20;particle=flame} @self ~onSpawn