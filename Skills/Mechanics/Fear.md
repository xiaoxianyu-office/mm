::include{file=/Skills/Mechanics/AuraComponents/Fear.md}
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