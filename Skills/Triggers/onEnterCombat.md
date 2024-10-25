## Description
Executes the skill when the mob enters combat.

> **REQUIRES [ThreatTables](/Mobs/ThreatTables) to be enabled**  

> The associated [@trigger](/Skills/Targeters/Trigger) is the entity that made the caster enter combat

## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Modules:
    ThreatTable: true
  Skills:
    # sends a message to all the players in the world
    # when the mob enters combat
    - message{m=ENTERED COMBAT} @World ~onEnterCombat
```