## Description
Causes the target entity to spin around for the given duration.  
When a mob casts the spin mechanic repeatedly it will move upwards while spinning.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| velocity  | v         | The velocity the target spins at                                     | 18      |

> This mechanic inherits every attribute of the [Aura](/Skills/Mechanics/Aura) mechanic

### Velocity Attribute
When you set velocity to 0, this mob's direction will be locked.


## Examples
```yaml
SpinningSpider:
  Type: SPIDER
  Skills:
  - spin{duration=100;velocity=20} @self ~onTimer:100
```


## Aliases
- [x] effect:spin
- [x] e:spin


<!--TAGS-->
<!--tag:Movement:Rotation-->
