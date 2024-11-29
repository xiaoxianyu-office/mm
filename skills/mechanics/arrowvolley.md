## Description

Fires a volley of arrows towards the target with a number of configurable properties.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | arrows, a | The number of arrows in the volley                                   | 20      |
| spread    | s         | How spread out the arrows are                                        | 45      |
| velocity  | v         | The velocity of the arrows                                           | 20      |
| fireTicks | ft, f     | The duration hit entities will burn for in ticks                     | 0       |
| removeDelay | rd, r   | The time the arrows will stay before disappearing in ticks           | 200     |
| canPickup | pickup    | Whether the arrows can be picked up by players                       | true    |
  
> Spread values must be very high to be noticed!

## Examples

This example will fire 20 arrows, with a spread of 25, at a speed of 10,
settings anything they impact on fire for 50 ticks (2.5 seconds), and
then remove themselves after 200 ticks (10 seconds).
```yaml
  Skills:
  - arrowvolley{a=20;s=25;v=10;f=50;rd=200} @Target
```


<!--TAGS-->
<!--tag:Projectile-->