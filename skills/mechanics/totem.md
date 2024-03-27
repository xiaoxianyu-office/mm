## Description
The totem mechanic places an invisible "totem", similar to the
[projectile](/skills/mechanics/projectile) mechanic, except that it
doesn't move. Much like projectiles, you can use onTick skills to create
effects in order to identify the totem's location.

Totems will pulse their onHit skill on any targets that come within
their defined radius until their charges or duration run out. They're
useful for creating ground effects with particles, such as clouds of
poison or land mines.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| Charges   | ch, c     | Determines how many times the totem can hit something before disappearing | 0  |
| YOffset   | yo        | How high off the target the totem will spawn                          | 1      |

> Inherits attributes from [Projectile](/skills/mechanics/projectile)
>> `stopAtEntity` gets **defaulted** to `false`


## Examples
```yaml
MyFirstTotem:
  Skills:
  - totem{ch=1;i=1;md=8;onTick=MFT_TICK} @self

MFT_TICK:
  Skills:
  - damage{a=3} @ENO{r=5}
```