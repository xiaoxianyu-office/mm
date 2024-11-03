## Description
Targets the specified coordinates in a world


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| location  | loc, l, c | The full location, in the `x,y,z,yaw,pitch` format                   |         |
| x         |           | If `location` is not set, it's the x coordinate of the target location | 0     |
| y         |           | If `location` is not set, it's the y coordinate of the target location | 0     |
| z         |           | If `location` is not set, it's the z coordinate of the target location | 0     |
| yaw       |           | If `location` is not set, it's the yaw of the target location         | 0      |
| pitch     |           | If `location` is not set, it's the pitch of the target location       | 0      |
| world     | w         | The world to target. If not set, it will target the caster's world    |        |


## Examples
```yaml
ExampleSkill:
  Skills:
  - setblock{m=DIAMOND_BLOCK} @Location{location=100,70,-120,0,0}
  - setblock{m=EMERALD_BLOCK} @Location{x=100;y=71;z=-120}
```


## Aliases
- [x] l
- [x] loc