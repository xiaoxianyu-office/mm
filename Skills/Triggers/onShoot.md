## Description
Executes the skill when the mob shoots a projectile.  
For example, skeletons with bows will shoot arrows; ghasts, blazes, or ender dragon will shoot some type of fireball.  

> The associated [@trigger](/Skills/Targeters/Trigger) is the caster

| [Implemented Placeholders](/Skills/Placeholders#variable-placeholders)     |
|--------------------------------|
| `<skill.var.bow-tension>`      |


## Implementations
- [MythicCrucible](/../../../mythiccrucible/-/wikis/Skills/Triggers/onShoot)
- [MythicRPG](/../../../mythicrpg/-/wikis/Skills/Triggers/onShoot)


## Examples
```yml
EXAMPLE_MOB:
  Type: SKELETON
  Skills:
    # sends a message to all the players in the world
    # when the skeleton shoots from a bow
    - message{m=I SHOT AN ARROW} @World ~onShoot
```


## Aliases
- [x] onBowShoot
- [x] onShootBow