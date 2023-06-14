## Description
Matches the number of players in the caster's world


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The number of players to check for. Can be a range                   | 0       |


## Examples
```yaml
  Conditions:
  - playersInWorld{amount=>5}
```