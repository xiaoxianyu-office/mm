Mechanic: TeleportTo
====================

Will teleport the targeted entity or entities to the specified location.

Attributes
----------

| Attribute             | Aliases   | Description                                                                   | Default Value |
|-----------------------|-----------|-------------------------------------------------------------------------------|---------------|
| location, coordinates | loc, l, c | The coordinates of the teleport-destination                                   |               |
| world                 | w         | The destination-world. Optional attribute if "location" is given              |               |
| yaw                   | y         | The yaw that the affected entities should assume                              | 0             |
| pitch                 | p         | The pitch that the affected entities should assume                            | 0             |
| relative                 | r        | Whether the location is relative or directional                | false              |
| targetasorigin                | tao         | Will use the target's location as the origin instead of the caster |  false             |

Examples
--------

Will teleport all players in a radius of 50 blocks around the casting
mob to the specified location:

    Skills:
    - teleportto{location=190,64,200} @PIR{r=50}