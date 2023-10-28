## Description

The Global Cooldown skill lets you set a mob's global
cooldown, used in conjunction with the [offgcd](skills/conditions/offgcd) condition if you want a
mob's abilities to have a global, over-all shared cooldown. This can be useful for allowing a mob to only use a single skill at a time rather than multiple by giving the cooldown to each skill the mob uses.

Attributes
----------

| Attribute | Aliases | Description                   | Default Value |
|-----------|---------|-------------------------------|---------------|
| ticks     | t       | How many ticks to set the GCD | 20            |

  

Examples
--------

This skill would trigger a Global Cooldown of 40 ticks, during which the
skill and all other skills using the [offgcd](skills/conditions/offgcd) condition would not be
usable.
```yaml
IceBolt:
  Conditions:
  - offgcd
  Skills:
  - gcd{ticks=40}
```