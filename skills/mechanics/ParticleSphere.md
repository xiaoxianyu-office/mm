## Description
Creates a sphere of particles at the targeted entity or location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the sphere to draw                                     | 0       |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic


## Examples
```yaml
FlameSphere:
  Skills:
  - particlesphere{particle=flame;amount=200;radius=5} @self
```


## Aliases
- [x] effect:particlesphere
- [x] e:ps
- [x] ps



<!--TAGS-->
<!--tag:Effect:Particle-->
