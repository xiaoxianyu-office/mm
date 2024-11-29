## Description
Summons an Ender Crystal which shoots a beam towards the target.

**Warning: This effect creates an Ender Crystal which can be exploded and cause block damage.**


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| duration  | d      | The time (in ticks) that the effect is active     | 60            |
| yoffset   | y, yo  | 	The default vertical offset from the casting mob | 0             |


## Examples
```yaml
EnderBeamSkill:
  Skills:
  - effect:enderbeam{d=100;y=2} @target
```


## Aliases
- [x] effect:enderbeam


<!--TAGS-->
<!--tag:Effect-->