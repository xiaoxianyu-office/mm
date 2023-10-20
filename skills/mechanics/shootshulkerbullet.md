================================

*Added in 4.12 MM*

## Description:

Shoots a shulker bullet at the target entity, giving them levitation on hit.

*Requires a target entity. Does not work well with location targeters.*

## Attributes:

| Attribute | Aliases | Description                                  | Default Value |
|-----------|---------|----------------------------------------------|---------------|
| interval  | i       | how often in ticks this mechanic updates     | 4             |
| onTick    | oT      | the skill this mechanic calls each interval  | NONE          |
| onHit     | oH      | the skill this mechanic calls when it hits the target | NONE |
| onEnd     | oE      | the skill this mechanic calls when it ends   | NONE          |


## Examples:

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