## Description
Executes the skill when the mob, must be a creeper, is primed (i.e. via the use of a flint and steel).  
  
> The associated [@trigger](/Skills/Targeters/Trigger) is the caster itself


## Examples
```yml
EXAMPLE_MOB:
  Type: CREEPER
  Skills:
    # sends a message to all the players in the world
    # when the mob is primed
    - message{m=OOO I'M GONNA EXPLODE} @World ~onPrime
```