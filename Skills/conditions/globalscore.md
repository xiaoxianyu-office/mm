## Description
Checks a global scoreboard value (the value associated with the fake player __GLOBAL__)


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| objective | obj, o    | The objective                                                        |         |
| value     | val, v    | The value to match                                                   |         |


## Examples
```yaml
  Conditions:
  - globalscore{o=KillCount;value=5} true
```


## Aliases
- [x] scoreglobal