## Description
Changes the rotation of the target (only works on non-player entities).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| relative  |           | If the change is relative to the target, boolean                     |         |
| yaw       |           | The new yaw                                                          | 0       |
| pitch     |           | The new pitch                                                        | 0       |


## Examples
```yaml
  Skills:
  - setrotation{relative=true;pitch=-45}
  - ...
```