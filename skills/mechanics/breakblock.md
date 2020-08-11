Mechanic: Break Block
=====================

Will break a block at the target location. This mechanic will also drop
the block (with exception of Bedrock). REQUIRES `forcesync=true`.

Attributes
----------

| Attribute | Aliases | Description | Default Value |
|-----------|---------|-------------|---------------|
|           |         |             |               |

  

Examples
--------

This example would break the block at location x:100,y:64,z:100 in the
current world when right-clicked.

      Skills:
      - breakblock{forcesync=true} @location{c=100,64,100} ~onInteract
      - ...
