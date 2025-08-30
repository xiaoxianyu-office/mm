## Description
Checks if the pitch of the target entity is within a range


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| pitch     | p         | The number range to match                                            |         |



## Examples
```yaml
  Conditions:
  - pitch{p=-45to45} true
```

```yaml
  Conditions:
  - pitch{p=>45} true
```