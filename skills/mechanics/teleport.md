Mechanic: Teleport
==================

Teleports the caster to the targeted location/entity. The end point of the teleportation will be within an area whose size depends on the `spreadh` and `spreadv` attributes.

Attributes
----------

| Attribute | Aliases | Description                                    | Default Value |
|-----------|---------|------------------------------------------------|---------------|
| spreadh   | sh      | The horizontal spread of the landing location. | 0             |
| spreadv   | sv      | The vertical spread of the landing location.   | 0             |

  

Special Notes
-------------

The skill will attempt to find a safe landing location within the spread
area, if possible, and should generally avoid putting the mob inside of
blocks.

Examples
--------

This example would teleport the mob to within 5 blocks of the targeted
player, on the same vertical axis.

```yaml
Warp:
  Skills:
  - teleport{spreadh=5;spreadv=0} @target
```