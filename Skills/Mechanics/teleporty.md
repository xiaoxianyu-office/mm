## Description
Teleports the caster to the specified Y coordinate.  
No target is required for this mechanic, as the caster will always be the one that is teleported.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| y         |           | Where to teleport on the Y axis                                      | 0       |


## Examples
This example would teleport the caster at its coordinates, but with Y with a value of 5.
```yaml
WarpY:
  Skills:
  - teleportY{y=5}
```

## Aliases
- [x] tpy


<!--TAGS-->
<!--tag:Movement:Teleport-->
