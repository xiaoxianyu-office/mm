## Description
Crates an [aura] that causes the holding mob to follow a path.  
This mechanic is also an [aura].


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| path      | p         | A list of either coordinates in the format `(x,y,z)` or [targeters]  |         |
| onGoalSkill| onGoal, og, then | The [metaskill] to execute when the last point is reached    |         |
| tolerance |           | The minimum distance the mob must be from each point in order to having "reached" it                                                                                   | 1.5     |
| speed     | s         | The speed multiplier of the movement                                 | 1       |
> This mechanic inherits every attribute of the [Aura] mechanic  
>> - The `auraname` attribute is **set** at `#pathing`
>> - The `duration` attribute is **defaulted** at `2147483647`
>> - The `charges` attribute is **set** at `1`  
>> - The `maxStacks` attribute is **set** at `1`  
>> - The `mergeAll` attribute is **set** at `true`  


## Examples
```yaml
  Skills:
  - followPath{
    speed=2;
    tolerance=2;
    path=(200,5,520),(200,5,500),@forward{a=5};
    onGoal=[
      - message{m="I DID IT"} @world
    ]} @self ~onInteract
```


## Aliases
- [x] path


<!-- LINKS -->
[aura]: skills/mechanics/aura
[metaskill]: Skills/Metaskills
[targeters]: Skills/Targeters