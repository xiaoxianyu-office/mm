## Description
Creates an explosion at the target entity or location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| yield       | y       | The yield (power) of the explosion                                   | 0.013   |
| blockdamage | bd      | (true/false) Whether the explosion will damage blocks                | false   |
| fire        | f,ft    | (true/false) Whether the explosion leaves fire behind                | false   |

> WARNING  
> Blockdamage doesn't seem to respect protection like WorldGuard regions. Use at your own risk


## Examples
```yaml
ExplosiveBlast:
  Skills:
  - explosion{yield=4} @target
```


## Aliases
- [x] explode


<!--TAGS-->
<!--tag:Damage-->
<!--tag:World-->