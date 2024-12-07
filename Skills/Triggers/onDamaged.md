## Description
Executes the skill when the mob takes damage.
> The associated [@trigger](/Skills/Targeters/Trigger) is the entity that dealt the damage

| [Implemented Placeholders](/Skills/Placeholders#variable-placeholders)     |
|--------------------------------|
| `<skill.var.damage-amount>`    |
| `<skill.var.damage-type>`      |
| `<skill.var.damage-cause>`     |


## Implementations
- [MythicCrucible](/../../../mythiccrucible/-/wikis/Skills/Triggers/onDamaged)


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob takes damage
    - message{m=DAMAGED} @World ~onDamaged
```


## Aliases
- [x] onHurt