## Description
Tests if the target is within the given angle from where the caster is looking.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| angle     | a         | The angle of the FOV to check in                                     | 90      |
| rotation  | r         | Rotates the FOV to check in                                          | 0       |


## Examples
```yaml
  TargetConditions:
  - fieldofview{angle=90} false
```
This condition will filter out every target that is within a 90 degree field of view of the caster.

##
```yaml
  TargetConditions:
  - fieldofview{angle=90} true
```
This condition will allow to be targeted only entities that are within a 90 degree field of view of the caster.


## Aliases
- [x] infieldofview
- [x] fov