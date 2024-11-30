## Description
Rotates the caster towards the target location, up to a maximum yaw/pitch increment from the current rotation. 


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| rotateyaw | yaw       | Whether yaw should be rotated                                        | true    |
| rotatepitch | pitch   | Whether pitch should be rotated                                      | false   |
| useEyeLocation | uel  | Whether the caster's eye location should be used as the base to calculate the new yaw/pitch                                                                                  | false   |
| maxyaw    | my, y     | The maximum increment the yaw can have                               | 0       |
| maxpitch  | mp, p     | The maximum increment the pitch can have                             | 0       |


## Examples
```yaml
SlowTurn:
  Skills:
  - rotatetowards{pitch=true;uel=true;maxyaw=1;maxpitch=0.5;repeat=199;repeatInterval=2} @Trigger ~onInteract
```


## Aliases
- [x] rotateto


<!--TAGS-->
<!--tag:Movement:Rotation-->
