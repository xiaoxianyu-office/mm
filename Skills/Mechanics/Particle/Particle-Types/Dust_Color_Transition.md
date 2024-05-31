## Particle
![img](/Skills/Mechanics/Particle/Particle-Types/images/DUST_COLOR_TRANSITION.gif)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| color | c, color1, c1, fromcolor, fc | The color the particles starts as | #FF0000 |
| color2 | c2, tocolor, tc | The color the particles transitions to | #0000FF |
| size |  | The size of the particle | 1 |
> This particle has a [Dusttransition](/Skills/Mechanics/Particle/Particle-Types#dusttransition) Datatype, and inherits all of its attributes



## Examples
```yaml
  Skills:
  - particle{p=dust_color_transition;color=#FF0000;color2=#0000FF;size=1}
```


## Aliases
- [x] dustcolortransition
- [x] dustcolor


