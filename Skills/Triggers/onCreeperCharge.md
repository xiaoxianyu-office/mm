## Description
Executes the skill when the casting creeper is charged.  

> The associated [@trigger](/Skills/Targeters/Trigger) is the caster itself


## Examples
```yml
EXAMPLE_MOB:
  Type: CREEPER
  Skills:
    # sends a message to all the players in the world
    # when the mob gets charge
    - message{m=CHARGED} @World ~onCreeperCharge
```


## Aliases
- [x] onCreeper_Charge
- [x] onCharged
- [x] onCharge