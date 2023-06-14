## Description
Checks the stance of the target mob.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| stance    | s         | The stance to match                                                  | DEFAULT |
| strict    | str       | Whether to match exactly                                             | false   |


## Examples
```yaml
  Conditions:
  - stance{s=CombatStance;str=true} true
```