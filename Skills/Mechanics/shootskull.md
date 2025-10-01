## Description
Shoots a wither skull from the mob towards the target entity or
location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| yield     | strength, y, s | The yield (power) of the skull's explosion.                     | 1       |
| playsound | ps        | Whether or not to play the skull launching sound when it is created  | false   |


## Examples
This example would shoot a barrage of 3 fast-moving Wither Skulls at the
target.
```yaml
SkullBarrage:
  Skills:
  - shootskull{y=1;v=4} @target
  - delay 10
  - shootskull{y=1;v=4} @target
  - delay 10
  - shootskull{y=1;v=4} @target
```


## Aliases
- [x] shootwitherskull
- [x] skull
- [x] witherskull


<!--TAGS-->
<!--tag:Projectile-->
