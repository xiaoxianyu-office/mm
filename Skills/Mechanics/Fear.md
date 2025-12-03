## Description
Applies an aura that makes the target run around in fear


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed | s | The fleeing speed of the entity | 0.35 |
| directionChangeInterval | dirchange, dci | How often, in ticks, the entity changes direction | 20 |
| feardistance | fearrange, fdist, fd | When the affected entity's distance from the caster is less than this value, it will try to run *away* form it instead of completely randomly | 10.0 |
| rotationticks | rotateticks, rt | A duration, in ticks, over which the entity's head will be rotated towards the new runnign direction | 5 |
> This mechanic inherits every attribute of the [Aura](/Skills/Mechanics/Aura) mechanic
>> - The `auragroup` attribute is **defaulted** at `#fear`


## Examples
```yaml
  Skills:
  - fear{speed=0.35f;directionchangeinterval=20;feardistance=10.0f;rotationticks=5} @self
```

<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
<!--tag:AI-->