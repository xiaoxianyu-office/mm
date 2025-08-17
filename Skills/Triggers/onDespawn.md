## Description
Executes the skill when the mob despawns.
> The associated [@trigger](/Skills/Targeters/Trigger) is the caster itself


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob despawns
    - message{m=DESPAWNED} @World ~onDespawn
```


## Aliases
- [x] onDespawned