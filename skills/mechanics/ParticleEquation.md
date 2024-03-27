# DISCLAIMER
**This mechanic is a Work In Progress. As such, it is not yet functional, examples for it are not available, and is not intended to be used.**


## Description 
Generates a particle effect based on an equation.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| equation  | eq        | The equation to use. Allows the `x`,`y`,`z` variables                | 0       |
| boundx    | bx        | The maximum width of the generated particles on the x axis           | 1       |
| boundz    | bz        | The maximum width of the generated particles on the z axis           | 1       |
| boundy    | by        | The maximum height of the generated particles on the y axis          | 1       |
| resolution | res      | The resolution of the equation                                       | 0.1     |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic


## Aliases
- [x] effect:particleeq
- [x] particleequation
- [x] particleeq