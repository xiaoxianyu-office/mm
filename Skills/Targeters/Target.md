## Description
Targets the caster's target.

- If the caster is a mob, targets its target
- If the caster is a player, targets the entity the player is looking at, if close enough

Note that some types of entities, such as the Ghast, because of their hardcoded ai, will never result to have a target, making this targeter useless on them

## Attributes
>*This targeter has no attributes*


## Examples
```yaml
ExampleSkill:
  Skills:
  - ignite @Target
```


## Aliases
- [x] T