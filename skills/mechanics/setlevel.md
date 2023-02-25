Mechanic: Set Level
===================

*Introduced in version 2.2.1*

Causes the casting mob to change it's level.

Possible operations for the action value are SET, ADD, SUBTRACT,
MULTIPLY, and DIVIDE.

Attributes
----------

| Attribute | Aliases | Description                            | Default Value |
|-----------|---------|----------------------------------------|---------------|
| action    | a       | Type of operation to perform           | SET           |
| level     | l       | Amount of levels used in the operation | 1             |

  

Examples
--------

This will set the mob level to 3 when it spawns
```yaml
    - setlevel{a=set;l=3} @self ~onSpawn
```

This will increase the mob level by 1 each time it kills a player
```yaml
    - setlevel{a=add;l=1} ~onKillPlayer
```

This will set the level of the mob to a random value between 1 and 5 when it spawns, plus the score of the `__GLOBAL__` fake player from the "testlevel" scoreboard. The usage of [Placeholders](/Skills/Placeholders) and [Math Operations](/Skills/Math) inside of a mechanic is **Premium Only**
```yaml
    - setlevel{a=set;l="<random.1to5> + <global.score.testlevel>"} @self ~onSpawn
```