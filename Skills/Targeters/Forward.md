## Description
Targets a location in front of the caster


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| forward   | f, amount, a | How distant should the targeted point be                          | 5       |
| rotate    | rot       | The rotation, around the caster, of the target location              | 0       |
| useeyelocation | uel  | If the eye location should be used as the base of the targeter       | false   |
| lockpitch |           | If the location should be targeted as if the caster has a pitch of 0 | false   |


## Examples
```yaml
ExampleSkill:
  Skills:
  - effect:particles @Forward{f=3;uel=true;rot=10}
```