Mechanic: TeleportIn
====================

Will teleport the target relative to where the mob is facing. The direction attribute must be in this format: direction=x,y,z

x is forward or backward

y is up or down

z is left or right

Attributes
----------

| Attribute             | Aliases   | Description                                                                   | Default Value |
|-----------------------|-----------|-------------------------------------------------------------------------------|---------------|
| direction | dir,d,vector,v | The direction to where the mob will be teleported                                 | |
| yaw | y | Yaw modifier | 0 | 
                
Examples
--------

Will teleport the caster one block to the right.

    Skills:
    - teleportin{direction=0,0,1} @Self