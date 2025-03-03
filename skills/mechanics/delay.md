## Description
Causes the current skilltree to be delayed by X ticks.  
Delay can also be used as an attribute directly inside of mechanics by adding the `delay=TICKS` [universal attribute](/Skills/Mechanics#universal-attributes). This way, the delay is not applied to the entire skilltree but only to the single mechanic.  

Skill-delay and Attribute-delay do not work in the same manner.

> This mechanic can also be used to accomplish [Intratick Scheduling](/Skills/Intratick-Scheduling)

## Examples
```yaml
Skills:
  - ignite{ticks=60}
  - delay 60
  - explode
```

This is an example of using the delay universal attribute. It will work inside any mechanic and will delay it from happening by the specified amount of ticks.
```yaml
Skills:
  - skill{skill=exampleskill;delay=200}
  - explode{delay=80}
```


<!--TAGS-->
<!--tag:Meta:Flow-->
