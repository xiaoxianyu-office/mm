## Description
Tests if the target's vanilla target is within a certain distance.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance  | d         | Distance to check                                                    | 0       |


## Examples
```yaml
  Conditions:
  - targetwithin{d=10} true
```
> This will check if the vanilla target of the casting entity is within 10 blocks

---
```yaml
  TargetConditions:
  - targetwithin{d=10} true
```
> This will check if the vanilla target of the inherited target is within 10 blocks of the caster... yikes! While it technically works, let's not use it this way!

