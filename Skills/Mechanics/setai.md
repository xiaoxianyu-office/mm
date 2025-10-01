## Description
Toggles the target AI


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| ai        | state, value | Sets the new mob AI. `true` enables it, `false` disables it       | false   |


## Examples
This example will turn off the ai of the mob for 5 seconds
```yaml
TemporaryAISwitcher:
  Skills:
  - setAI{ai=false} @self
  - delay 100
  - setAI{ai=true} @self
```


## Aliases
- [x] ai


<!--TAGS-->
<!--tag:AI-->
