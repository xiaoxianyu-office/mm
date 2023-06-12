## Description
Checks if the target location is **not** within the given WorldGuard region


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| region    | r, name, n| The region's name                                                    |         |


## Examples
```yaml
  Conditions:
  - notinregion{r=BossZone} true
```