## Description
Executes a skill when the mob's special projectile type (trident, snowball, wither skull, llama's spit etc) lands on the ground without hitting an entity.

### Compatible Projectiles
[> Reference onProjectileHit's <](/Skills/Triggers/onProjectileHit#compatible-projectiles)


## Examples
```yaml
YourAverageDrowned:
  Type: DROWNED
  Equipment:
  - TRIDENT HAND
  Skills:
  - message{m="Awww..."} @target ~onProjectileLand
```


## Aliases
- [x] onProjectile_Land
- [x] onTridentLand