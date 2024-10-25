## Description
Executes the skill when the mob changes target.

> **REQUIRES [ThreatTables](/Mobs/ThreatTables) to be enabled**


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Modules:
    ThreatTable: true
  Skills:
    # sends a message to all the players in the world
    # when the mob's target changes
    - message{m=Target Changed} @World ~onChangeTarget
```


## Aliases
- [x] onTargetChange