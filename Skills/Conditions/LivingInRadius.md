## Description
Matches a range to how many living entities are in the given radius


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount to check for                                              | 1       |
| radius    | r         | The radius of the search                                             | 5       |


## Examples
```yaml
  Conditions:
  - livinginradius{a=<5;r=10} true
```