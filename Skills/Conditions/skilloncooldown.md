## Description
Checks if the given skill is in cooldown for the target entity


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| skill     | s         | The metaskill to check                                               |<!--type:MetaSkill-->|


## Examples
```yaml
  TargetConditions:
  - skillOnCooldown{skill=TestSkill}
```