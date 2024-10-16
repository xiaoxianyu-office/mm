## Description
Matches the number of players online


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The number of players to check for. Can be a range                   | 0       |


## Examples
```yaml
  Conditions:
  - playersOnline{amount=>5}
```


## Aliases
- [x] onlineplayercount
- [x] onlineplayers