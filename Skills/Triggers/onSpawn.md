## Description
Executes the skill when the mob spawns.  
> There is no associated [@trigger]


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob spawns
    - message{m=SPAWN} @World ~onSpawn
```


<!-- LINKS -->
[ThreatTables]: /Mobs/ThreatTables
[@trigger]: /Skills/Targeters/Trigger