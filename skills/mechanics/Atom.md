## Description 
Creates an orbiting Atom effect at the location.            


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| particleorbital | particleo, po | The [particle] that will be displayed at the orbitals     |`particle`<!--type:Particle-->|
| particlenucleus | particlen, pn | The [particle] that will be displayed at the nucleus       | reddust<!--type:Particle-->|
| amountnucleus | amountn, apn, an | The amount of particles for the nucleus                   | 50      |
| orbitals  | o         | The amount of orbitals around the nucleus                            | 2       |
| amountorbital | amounto, apo, ao | The amount of particles for each orbital                  | 1       |
| radius    | r         | The radius of the orbitals                                           | 4       |
| radiusnucleus | rn    | The radius of the nucleus                                            | 1       |
| rotation  | ro        | The rotation of the atom                                             | 0       |
| ticks     | t         | The amount of ticks during which the atom will persist               | 1       |
| interval  | in        | The interval of the updates of the atom                              | 10      |
| velocity  | v         | The velocity of the atom                                             | 80      |
> This mechanic inherits every attribute of the [particle](/skills/mechanics/Particle) mechanic


## Examples
```yaml
  Skills:
  - Atom{p=reddust;r=2;d=true;dr=true;dir=1,0,0;ticks=20} @selflocation{y=2} ~onSwing
```


## Aliases
- [x] effect:atom
- [x] e:atom


<!-- LINKS -->
[particle]: /Skills/Mechanics/Particle/Particle-Types


<!--TAGS-->
<!--tag:Effect:Particle-->