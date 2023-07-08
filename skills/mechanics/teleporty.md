Mechanic: TeleportY
==================

Teleports the caster up or down.

Attributes
----------

| Attribute | Aliases | Description                                    | Default Value |
|-----------|---------|------------------------------------------------|---------------|
| y   |       | The vertical distance to teleport | 0 |

  

Special Notes
-------------

The skill will attempt to find a safe landing location and should generally avoid putting the mob inside of
blocks.

Examples
--------

This example would teleport the mob 5 blocks up.

```yaml
WarpY:
  Skills:
  - teleportY{y=5} @target
```