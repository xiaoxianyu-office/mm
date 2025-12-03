## Description
Runs a given metaskill for each pin in a multi-pin


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| name | n, pin, p, key, k | The name of the pin | |
> This mechanic inherits every attribute of the [Skill](/skills/mechanics/skill) mechanic


## Examples
```yaml
  Skills:
  - foreachpin{name=YourCoolPin;skill=[
    - particle{p=flame;a=20}
    ]} @self
```