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
| stopatentity | se     | Whether the totem should terminate upon hitting an entity             | false  |
| hugsurface| hs        | Whether or not the totem should be aligned with the ground           | false   |
| hugliquid | hugwater, huglava | Whether, when using hugSurface, a liquid can also count as a "surface" the totem can align itself with | false   |
| heightfromsurface| hfs| How high above the surface the totem should align itself if HugSurface is set to true | 0.5     |
| faceawayfromcaster | fafc | Whether the totem should face away from the caster when first placed | false |
> Inherits attributes from [Projectile](/skills/mechanics/projectile)


## Examples
```yaml
MyFirstTotem:
  Skills:
  - totem{ch=1;i=1;md=8;onTick=MFT_TICK} @self

MFT_TICK:
  Skills:
  - damage{a=3} @ENO{r=5}
```


## Aliases
- [x] toteme
- [x] t


<!--TAGS-->
<!--tag:Meta-Mechanic-->