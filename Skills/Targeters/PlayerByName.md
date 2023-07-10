## Description
Targets a specific player by their name. Can be a placeholder.

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| name      | n         | The name of the player                                               | CarsonJF|


## Examples
The following mob will remeber the name of the player that first hit it after it spawned, and will continue to ignite them every 10 seconds after that
```yaml
VengefulMob:
  Type: ZOMBIE
  Skills:
  - setvariable{var=caster.targetedplayer;type=STRING;val=<trigger.name>} @self ~onDamaged =100% ?~isPlayer
  - ignite @PlayerByName{name=<caster.var.targetedplayer>} ~onTimer:200 ?variableisset{var=caster.targetedplayer}
```


## Aliases
- [x] specificplayer