## Description
Executes the skill when the mob spawns.  
> There is no associated [@trigger](/Skills/Targeters/Trigger)


## Implementations
- [MythicCrucible](/../../../mythiccrucible/-/wikis/Skills/Triggers/onSpawn)
- [MythicRPG](/../../../mythicrpg/-/wikis/Skills/Triggers/onSpawn)


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob spawns
    - message{m=SPAWN} @World ~onSpawn
```