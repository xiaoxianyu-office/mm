## Description
Rallies nearby mobs of the given types to focus-attack the given target.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| types     | type, t   | A list of mob types to rally. The list can include both Mythic Mob types and regular Entity types                                                                           |<!--type:Mob--><!--list-->|
| radius    | r, hradius, hr | The radius (in blocks) in which to search for mobs to rally     | 10      |                                                              
| vradius   | vr        | Overrides the vertical component of the radius.                      | radius  |
| overwritetarget | ot      | Whether to rally mobs that already have a target                 | true    |
| rallyconditions | conditions, cond, c | A list of conditions that the entities must pass in order to be rallied                                                                                        |<!--type:Conditions-->|
  

## Examples
This example would cause all mobs of the type "Guard" or "Knight" within
30 blocks, that don't already have a target, to attack the whatever or
whoever triggered this skill.
```yaml
CallForHelp:
  Skills:
  - message{m="<caster.name><&co> Guards! Help me!"} @PlayersInRadius{r=30}
  - rally{types=Guard,Knight;radius=30;ot=false} @Trigger
```


## Aliases:
- [x] callforhelp


<!--TAGS-->
<!--tag:Threat-->