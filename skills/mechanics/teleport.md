## Description
Teleports the caster to the targeted location/entity. The end point of the teleportation will be within an area whose size depends on the `spreadh` and `spreadv` attributes.

The skill will attempt to find a safe landing location within the spread
area, if possible, and should generally avoid putting the mob inside of
blocks. The unsafe attribute will allow mobs to teleport into the target entity.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| spreadh   | sh        | The horizontal spread of the landing location.                       | 0       |
| spreadv   | sv        | The vertical spread of the landing location.                         | 0       |
| unsafe    | us        | Avoids finding a safe teleport (will ignore sH and sV)               | 0       |


## Examples
This example would teleport the mob to within 5 blocks of the targeted
player, on the same vertical axis.
```yaml
Warp:
  Skills:
  - teleport{spreadh=5;spreadv=0} @target
```