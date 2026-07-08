## Description
Targets a specific entity by their UUID. Can be a placeholder.  
The uuid option also accepts a comma-separated list of UUIDs to target multiple entities at once. Entries that are not valid UUIDs are silently skipped.  
This targeter will target anything, regardless of targeter filters


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| uuid      | u         | The uuid, or comma-separated list of uuids, of the entity(s)         | 0       |


## Examples
The following mob will remember the uuid of the entity that first hit it after it spawned, and will continue to ignite them every 10 seconds after that
```yaml
VengefulMob:
  Type: ZOMBIE
  Skills:
  - setvariable{var=caster.targetedentity;type=STRING;val=<trigger.uuid>} @self ~onDamaged =100% ?~isLiving
  - ignite @UniqueIdentifier{uuid=<caster.var.targetedentity>} ~onTimer:200 ?variableisset{var=caster.targetedentity}
```

You can also pass several UUIDs at once as a comma-separated list to target every matching entity in one skill. The following ignites three entities by their UUIDs.
```yaml
IgniteMany:
  Skills:
  - ignite @UUID{u="9b7f8e2a-1c3d-4e5f-8a90-1234567890ab,3f2c1d0e-5a6b-7c8d-9e0f-abcdef012345,0a1b2c3d-4e5f-6789-0abc-def012345678"}
```


## Aliases
- [x] uuid