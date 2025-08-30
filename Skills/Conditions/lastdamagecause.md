## Description
Checks the target's last damage cause.  
You can find a list of valid damage causes on the [Spigot Javadoc](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html)


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| damagecause | cause, c | The damage cause to match                                     | ENTITY_ATTACK<!--type:DamageCause-->|


## Examples
```yaml
  Conditions:
  - lastdamagecause{c=ENTITY_ATTACK} true
```