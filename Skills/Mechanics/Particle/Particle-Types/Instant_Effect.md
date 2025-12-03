## Particle
![img](/Skills/Mechanics/Particle/Particle-Types/images/INSTANT_EFFECT.gif)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| color | c | The color of the particle | #FF0000 |
| power | p | The power of the spell particle | 1 |
> This particle has a [Spell](/Skills/Mechanics/Particle/Particle-Types#spell) Datatype, and inherits all of its attributes



## Examples
```yaml
  Skills:
  - particle{p=instant_effect;color=#FF0000;power=1}
```


## Aliases
- [x] spell_instant
- [x] instant_spell


> This particle has a different name in versions before 1.20.5  
> - [x] spell_instant


