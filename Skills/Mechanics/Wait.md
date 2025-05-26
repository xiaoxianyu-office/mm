## Description
Puts the metaskill on hold (like the [delay](/skills/mechanics/delay) mechanic) until a set of conditions is met.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| conditions | cond, c, until | Conditions to check against. When the conditions are met, the metaskill will continue |<!--type:Conditions-->|
| interval | i | How often, in ticks, the mechanic should check against its condition          | 1       |
| timeout | timeouttime, tt | The maximum amount of ticks to wait before the metaskill is put out of hold even if conditions aren't met                                                                  | 200     |
| cancelSkill | cancel, cs | Whether, once a timeout happens, the metaskill should cancel execution instead of resuming                                                                            | false   |
| cancelConditions | cc, unless | A set of conditions that, if met, will make the mechanic resolve and the metaskill resume immediatly, like if the primary set of `conditions` was met      |<!--type:Conditions-->|


## Examples
```yaml
GroundSlam:
  Skills:
  - jump{v=5}
  - delay 5
  - wait{cond=[ - onground ];tt=300}
  - explode
```


<!--TAGS-->
<!--tag:Meta:Flow-->
<!--tag:Meta-Mechanic:Thenable-->