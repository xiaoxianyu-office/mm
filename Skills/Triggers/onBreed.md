## Description
Executes the skill when the mob breeds with another mob.

> This trigger has [`@Father`](/Skills/Targeters/Father) and [`@Mother`](/Skills/Targeters/Mother) targeters.

> The associated [@trigger](/Skills/Targeters/Trigger) is the player that made the caster breed


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob breeds
    - message{m=LET'S GET THIS BREAD} @World ~onBreed
```