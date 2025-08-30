## Description
Matches the target's health percentage or multiplier


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| percent   | p, healthpercent, hp | The health percentage or multiplier to check for (e.g., 50% or 0.5)  | 0       |
| includeabsorption | ia | Whether any absorption-related health should be factor into the calculation | false |

## Examples

```yaml
# Exactly at 50% health
Conditions:
- healthpercent{p=50%} true
```

```yaml
# Below 50% health
Conditions:
- healthpercent{p=<50%} true
```

```yaml
# Above 10% health
Conditions:
- healthpercent{p=>0.1} true
```

## Aliases
- [x] hppercent