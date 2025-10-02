## Description
Creates a box of particles at the targeted entity or location. 


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the box to draw                                        | 5       |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic


## Examples
```yaml
ParticleCube:
  Skills:
  - particlebox{particle=flame;amount=200;radius=5} @self
```


## Aliases
- [x] effect:particlebox
- [x] e:pb
- [x] pb


<!--TAGS-->
<!--tag:Effect:Particle-->
