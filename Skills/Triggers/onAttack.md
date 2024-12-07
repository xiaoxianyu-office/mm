## Description
Executes the skill when the mob attacks an entity.
> The associated [@trigger](/Skills/Targeters/Trigger) is the entity that was attacked

| [Implemented Placeholders](/Skills/Placeholders#variable-placeholders)     |
|--------------------------------|
| `<skill.var.damage-amount>`    |
| `<skill.var.damage-type>`      |
| `<skill.var.damage-cause>`     |


## Implementations
- [MythicCrucible](/../../../mythiccrucible/-/wikis/Skills/Triggers/onAttack)


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Damage: 1
  Skills:
    # sends a message to all the players in the world
    # when the mob attacks an entity
    - message{m=ATTACK} @World ~onAttack
```


## Aliases
- [x] onHit