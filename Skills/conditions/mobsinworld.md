## Description
Matches a range to how many mobs are in the target world


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The number range to match                                            | 0       |


## Examples
```yaml
  Conditions:
  - mobsinworld{a=20to50} true
```

```yaml
  Conditions:
  - mobsinworld{a=<50} true
```