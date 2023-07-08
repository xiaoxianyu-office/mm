## Description
Teleports the caster up or down.  
The skill will attempt to find a safe landing location and should generally avoid putting the mob inside of blocks.  
No target is required for this mechanic, as the caster will always be the one that is teleported.

## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| y         |           | The distance to teleport on the y axis                               | 0       |


## Examples
This example would teleport the caster 5 blocks up.
```yaml
WarpY:
  Skills:
  - teleportY{y=5}
```


## Aliases
- [x] tpy