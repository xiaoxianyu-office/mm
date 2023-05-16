## Description
Tests if the target is within the given angle from where the caster is looking


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| angle     | a         | The angle of the FOV to check in                                     | 90      |
| rotation  | r         | Rotates the FOV to check in                                          | 0       |


## Examples
```yaml
TargetConditions:
- fieldofview{angle=90} true
```


## Aliases
- [x] infieldofview
- [x] fov