## Description
Tests if the target has a scoreboard tag


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| tag       | t         | The tag to check for                                                 |         |


## Examples
```yaml
  Conditions:
  - hastag{t=KilledBoss1} true
```

```yaml
  TargetConditions:
  - hastag{t=PuzzleRoom1Solved} true
```


## Aliases
- [x] hasScoreboardTag