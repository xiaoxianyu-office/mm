## Description
Targets a specific entity by their UUID. Can be a placeholder.  
This targeter will target anything, regardless of targeter filters


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| uuid      | u         | The uuid of the entity                                               | 0       |


## Examples
The following mob will remember the uuid of the entity that first hit it after it spawned, and will continue to ignite them every 10 seconds after that
```yaml
VengefulMob:
  Type: ZOMBIE
  Skills:
  - setvariable{var=caster.targetedentity;type=STRING;val=<trigger.uuid>} @self ~onDamaged =100% ?~isLiving
  - ignite @UniqueIdentifier{uuid=<caster.var.targetedentity>} ~onTimer:200 ?variableisset{var=caster.targetedentity}
```


## Aliases
- [x] uuid