Mechanic: Hide From Players
===================

Hides the caster, if the caster is a player, from other players for a set duration.  
Caster will become a **vanilla** mob when it isn't a player.

Attributes
----------

| Attribute   | Aliases | Description       | Default Value |
|-------------|---------|-------------------|---------------|
| duration    | d       | The given duration |  |

Added in MM 4.13

------------

Examples
--------

    Skills:
    - hidefromplayers{d=100} ~onUse