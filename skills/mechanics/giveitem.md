Mechanic: Give Item
===================

Gives an item to the target

Attributes
----------

| Attribute | Aliases | Description       | Default Value |
|-----------|---------|-------------------|---------------|
| item      | i       | The item material |               |
| amount    | a       | The amount given  | 1             |

  

Examples
--------

    Skills:
    - giveitem{i=diamond_sword;a=1} @PIR{r=20} ~onSpawn
    - ...
