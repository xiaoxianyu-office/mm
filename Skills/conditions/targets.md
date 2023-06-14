## Description
Checks if the number of inherited targets from the parent skilltree matches the given range.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | Range of how many targets to check for                               | >0      |


## Examples
```yaml
  Conditions:
  - targets{a=>0} true
```

```yaml
  Conditions:
  - targets{a=0to5} true
```