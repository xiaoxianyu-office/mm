## Description
Changes the rotation of the target (only works on non-player entities).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| relative  | r, rel    | If the change is relative to the target, boolean                     | false   |
| yaw       | y         | The new yaw                                                          | 0       |
| pitch     | p         | The new pitch                                                        | 0       |


## Examples
```yaml
  Skills:
  - setrotation{relative=true;pitch=-45}
  - ...
```


## Aliases
- [x] setrot


<!--TAGS-->
<!--tag:Movement:Rotation-->
