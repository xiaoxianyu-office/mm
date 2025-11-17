## Description
Applies an aura to the target that makes it bouncy


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onBounceSkill | onbounce, ob | The metaskill to execute on bounce                            |<!--type:Metaskill-->|
| cancelevent | ce, canceldamage, cd | Whether to cancel fall damage for the duration of the aura| false |
> This mechanic inherits every attribute of the [Aura](Skills/Mechanics/Aura) mechanic


## Examples
```yaml
ExampleSkill:
  Skills:
  - bouncy{auraName=bounce;onBounceSkill=ExampleSkill2;ce=true} @target

ExampleSkill2:
  Skills:
  - ignite
```


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->