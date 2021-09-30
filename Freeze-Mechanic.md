Mechanic: Freeze 
================

Freezes the target for the given number of ticks using the Powdered Snow freezing effect. (requires 1.17)

Attributes
----------

| Attribute | Aliases      | Description                           | Default |
|-----------|--------------|---------------------------------------|---------|
| ticks     | t | How many ticks the target should freeze | 60      |

  

Examples
--------

      Skills:
      - freeze{ticks=100} @trigger ~onAttack

Freezes the entity that the mob using this skill is attacking for 100
ticks (5 seconds).