## Description
Targets the last entity that attacked the caster, if the caster is of the `INTERACTION` [Type](/Mobs/Mobs#type).


## Attributes
> *This condition has no attributes*


## Examples
The following example would ignite the last entity that attacked the caster once every 100 ticks
```yaml
ExampleInteractionEntity:
  Type: INTERACTION
  Skills:
  - ignite @interactionLastAttacker ~onTimer:100
```


## Aliases
- [x] lastAttacker