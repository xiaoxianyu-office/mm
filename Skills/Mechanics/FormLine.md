## Description
Makes the casting mob follow a linear path to a location


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| path      | p         | A list of either coordinates in the format `(x,y,z)` or [targeters]  |         |
| onGoalSkill| onGoal, og, then | The [metaskill] to execute when the last point is reached    |<!--type:Metaskill-->|
| tolerance |           | The minimum distance the mob must be from each point in order to have "reached" it                                                                                   | 2       |
| speed     | s         | The speed multiplier of the movement                                 | 1       |
| duration  | ticks, t, d, time, t | The maximum duration of the mechanic. Unless set, it's the maximum possible value for an integer                                                                  |         |

> This mechanic inherits every attribute of the [Aura](/Skills/Mechanics/Aura) mechanic


## Examples
```yaml
  Skills:
  - formline{
    speed=2;
    tolerance=2;
    path=(200,5,520),(200,5,500),@forward{a=5};
    onGoal=[
      - message{m="I DID IT"} @world
    ]} @self ~onInteract
```


## Aliases
- [x] lineup


<!--TAGS-->
<!--tag:Movement-->
<!--tag:Meta-Mechanic:Aura-->
<!--tag:AI-->