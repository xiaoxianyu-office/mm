## Description
Executes the skill when the mob drops combat.

> **REQUIRES [ThreatTables](/Mobs/ThreatTables) to be enabled**  

> There is no associated [@trigger](/Skills/Targeters/Trigger)


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Modules:
    ThreatTable: true
  Skills:
    # sends a message to all the players in the world
    # when the mob enters combat
    - message{m=DROPPED COMBAT} @World ~onDropCombat
```


## Aliases
- [x] onLeaveCombat
- [x] onCombatDrop
- [x] onExitCombat