## Description

The Global Cooldown skill lets you set a caster's global
cooldown, used in conjunction with the [offgcd](/skills/conditions/offgcd) condition if you want a
mob's abilities to have a global, over-all shared cooldown. This can be useful for allowing a mob to only use a single skill at a time rather than multiple by giving the cooldown to each skill the mob uses.  
> This is a no-target mechanic, and the affected entity will always be the caster

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| ticks     | t       | How many ticks to set the GCD | 20            |

  

## Examples
This skill would trigger a Global Cooldown of 40 ticks, during which the
skill and all other skills using the [offgcd](/skills/conditions/offgcd) condition would not be
usable.
```yaml
IceBolt:
  Conditions:
  - offgcd
  Skills:
  - gcd{ticks=40}
```

## Aliases
- [x] gcd
- [x] setgcd
- [x] setglobalcooldown


<!--TAGS-->
<!--tag:Meta-->
