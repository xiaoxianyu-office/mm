## Description
Matches the target's health


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| health    | h, amount, a | The health range to check for                                     | 0       |
| includeabsorption | ia | Whether any absorption-related health should be factor into the calculation | false |

## Examples

```yaml
Conditions:
- health{h=50} true
```

```yaml
# Below 50 health
Conditions:
- health{h=<50} true
```

```yaml
# Above 10 health
Conditions:
- health{h=>10} true
```

## Aliases
- [x] hp