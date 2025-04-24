## Description
Executes a skill when the mob's special projectile type (trident, snowball, wither skull, llama's spit etc) hits an entity.

> The associated [@trigger](/Skills/Targeters/Trigger) is the entity that has been hit

| [Implemented Placeholders](/Skills/Placeholders#variable-placeholders)     |
|--------------------------------|
| `<skill.var.damage-amount>`    |
| `<skill.var.damage-type>`      |
| `<skill.var.damage-cause>`     |

### Compatible Projectiles
| Casting Entity Type | Projectile |
|---------------------|------------|
| BLAZE               | SMALL_FIREBALL |
| ENDER_DRAGON        | DRAGON_FIREBALL |
| GHAST               | FIREBALL |
| LLAMA               | LLAMA_SPIT |
| WITHER              | WITHER_SKULL |
| DROWNED             | TRIDENT |
| SNOW_GOLEM          | SNOWBALL |


## Examples
```yaml
NotYourAverageDrowned:
  Type: DROWNED
  Equipment:
    - TRIDENT HAND
  Skills:
  - modifyDamage{a=3;modifier=MULTIPLY;sync=true} ~onProjectileHit
```


## Aliases
- [x] onProjectile_Hit
- [x] onTrident_Hit
- [x] onTridentHit