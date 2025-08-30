## Description
Checks the stance of the target mob.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| stance    | s         | The stance to match                                                  | DEFAULT |
| strict    | str       | Whether to match exactly. Checks if the current stance contains this word if set to false                                             | true    |


## Examples
```yaml
  Conditions:
  - stance{s=CombatStance;str=true} true
```