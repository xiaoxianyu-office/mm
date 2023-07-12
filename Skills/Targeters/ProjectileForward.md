## Description
Targets a location in front of the casting projectile, relative to its direction


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| forward   | f, amount, a | How far ahead should the targeted point be                        | 1       |
| rotate    | rot       | The rotation, around the projectile, of the target location          | 0       |


## Examples
```yaml
ExampleSkill:
  Skills:
  - projectile{...;
    onTick=[
      - effect:particles{p=flame} @ProjectileForward{f=2}
      - effect:particles @Origin
    ]}
```