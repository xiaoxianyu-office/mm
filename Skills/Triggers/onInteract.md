## Description
Executes the skill when a player interacts with, or *right-clicks*, the mob.  
> The associated [@trigger](/Skills/Targeters/Trigger) is the player that interacted with the caster


## Implementations
- [MythicCrucible](/../../../mythiccrucible/-/wikis/Skills/Triggers/onInteract)
- [MythicRPG](/../../../mythicrpg/-/wikis/Skills/Triggers/onInteract)


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when a player right-clicks the mob
    - message{m=INTERACTED} @World ~onInteract
```