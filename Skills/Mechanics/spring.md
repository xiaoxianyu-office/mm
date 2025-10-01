## Description
Creates a temporary "spring" of liquid at the target entity or location.

> Liquid spread from the spring can and will destroy any blocks that are
normally destroyed by liquids. Use wisely


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | The type of spring. Can be `water` or `lava`                         | water<!--type:Fluid-->|
| duration  | d         | The duration (in ticks) the spring will last                         | 40      |


## Examples
Creates a spring of water under the target for 5 seconds.
```yaml
Flood:
  Skills:
  - spring{d=100} @target
```


## Aliases
- [x] water


<!--TAGS-->
<!--tag:World-->
