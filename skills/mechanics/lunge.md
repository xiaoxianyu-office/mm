Mechanic: Lunge
===============

Applies forward directional velocity to the target.

Attributes
----------

| Attribute | Aliases | Description                                                   | Default Value |
|-----------|---------|---------------------------------------------------------------|---------------|
| velocity  | v       | The horizontal velocity at which the entity is moved forward. | 1             |
| velocityY | vy      | The vertical velocity at which the entity is moved forward.   | 1             |
| oldmath   | old, o  | If the lunge mechanic should use the old math formula         | false         |

  

Examples
--------

    - lunge{velocity=15;velocityY=5} @Self