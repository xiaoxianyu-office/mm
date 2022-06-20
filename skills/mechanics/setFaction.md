Mechanic: setFaction
=================

Sets or changes the target mob's faction.

Attributes
----------

| Attribute | Aliases    | Description                                                                                                    | Default Value |
|-----------|------------|----------------------------------------------------------------------------------------------------------------|---------------|
| faction  |  | The name of the faction to apply to the mob. | NONE          |

Examples
--------

    Skills:
    - setFaction{faction=Hostile} @self ~onSpawn

Sets the faction of the mob to "Hostile" when the mob spawns.