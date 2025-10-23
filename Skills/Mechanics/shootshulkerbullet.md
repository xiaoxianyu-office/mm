## Description
Shoots a shulker bullet at the target entity, giving them levitation on hit.

> Requires a target entity. Does not work well with location targeters


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | The type of the bullet                                               | arrow   |
| damage    | d         | The damage of the bullet                                             | 5       |
| bounce    |           | Whether the bullet should bounce                                     | false   |
| interval  | int, i    | how often in ticks this mechanic updates                             | 4       |
| onTick    | oT, m, meta, ontickskill, s, skill | the skill this mechanic calls each interval |<!--type:Metaskill-->|
| onHit     | oH, onhitskill | the skill this mechanic calls when it hits the target           |<!--type:Metaskill-->|
| onEnd     | oE, onendskill | the skill this mechanic calls when it ends                      |<!--type:Metaskill-->|
| startyoffset | syo    | The starting y offset of the bullet                                  | 0       |
| forwardoffset | startfoffset, sfo | The forward offset of the bullet                         | 0       |
| fromorigin | fo | Whether to shoot the shulker bullet from the origin                        | false   |


## Examples
This example would shoot a shulker bullet with some smaller white reddust particles in the onTick and onEnd. It would also damage the target for 5 damage when it hits them.

```yaml
TestingShootShulkerBullet:
  Skills:
  - ShootShulkerBullet{oT=TSSB_oT;oH=TSSB_oH;oE=TSSB_oE;i=1} @target
  
TSSB_oT:
  Skills:
  - particles{particle=reddust;color=#ffffff;size=0.66;a=2;hs=0;vs=0;s=0;y=0} @origin
TSSB_oH:
  Skills:
  - damage{a=5}
TSSB_oE:
  Skills:
  - particlesphere{particle=reddust;color=#ffffff;size=0.66;a=30;r=1;hs=0;vs=0;s=0;y=0} @origin
```


## Aliases
- [x] shootshulker


<!--TAGS-->
<!--tag:Projectile-->
<!--tag:Meta-Mechanic-->