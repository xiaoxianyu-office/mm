## Description
Targets all items in a radius around the origin of the metaskill


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 5       |

## Examples
In this example, a projectile launched by a player will make the caster pick up every item in a 5 block radius around the projectile every execution of the onTick metaskill
```yaml
ExampleSkill:
  Skills:
  - projectile{...;
    onTick=[
      - pickupitem @ItemsNearOrigin{r=5}
    ]}
```


## Aliases
- [x] INO