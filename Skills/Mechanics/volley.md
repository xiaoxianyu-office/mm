## Description
Shoots a volley of arrows or item-projectiles at the targeted entity or
location that deals damage. Can use any attribute from the Shoot
mechanic.


## Attributes
| Attribute | Aliases | Description                                       | Default |
|-----------|---------|---------------------------------------------------|---------|
| amount    | a       | The amount of projectiles                         | 10      |
| source    | s       | The type of the volley. Can be REGULAR or RAIN    | REGULAR<!--type:REGULAR,RAIN-->|
| radius    | r       | The radius of the volley                          | 1       |
| yoffset   | y       | The y offset of the target location of the projectiles | 0  |
| canPickup   | pickup  | Whether the arrows can be picked up by players             | true    |
> This mechanic inherits every *inheritable* attribute of the [Shoot](/Skills/Mechanics/Shoot) mechanic


## Examples
```yaml
  Skills:
  - volley{type=EGG;velocity=5;damage=10;amount=20}
```


## Aliases
- [x] shootvolley


<!--TAGS-->
<!--tag:Projectile-->
<!--tag:Meta-Mechanic-->

