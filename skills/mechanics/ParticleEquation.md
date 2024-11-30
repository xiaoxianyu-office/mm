# DISCLAIMER
**This mechanic is a Work In Progress. As such, it is not yet functional, examples for it are not available, and is not intended to be used.**


## Description 
Generates a particle effect based on an equation.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| equation  |           | The equation to use. Allows the `x`,`y`,`z` variables                | 0       |
| precision |           | The distance between individual particles                            | 1       |
| tolerance |           | Tolerance for floating points errors                                 | 0.1     |
| variables |           | A map of variables for the equation expression, like x/y/z are, separated by `;`<br>for example, `variables="h=1;t=2"` |  |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic


## Aliases
- [x] effect:particleequation
- [x] particleequation
- [x] e:peq
- [x] peq



<!--TAGS-->
<!--tag:Effect:Particle-->
