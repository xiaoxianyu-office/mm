## Description
Causes a geyser of liquid to shoot out of the ground at the targeted entity or location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | The type of liquid. Can be “WATER” or “LAVA”                         | WATER<!--type:Fluid-->|
| height    | h         | How high the geyser will go. Will be set to *at least* 1 even if specified otherwise. | 3       |
| interval  | i, speed, s | The interval (in ticks) between each iteration of the geyser animation | 10  |
| audience  |           | The [audience] of the effect                                         | nearby<!--type:Audience--> |


## Examples
```yaml
GeyserSkill:
  Skills:
  - geyser{type=LAVA;height=3;speed=10} @selflocation
```


## Aliases
- [x] effect:geyser
- [x] e:geyser


<!-- LINKS -->
[audience]: /Skills/Audience


<!--TAGS-->
<!--tag:Effect-->