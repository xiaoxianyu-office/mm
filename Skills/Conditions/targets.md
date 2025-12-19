## Description
Checks if the number of inherited targets from the parent skilltree matches the given range.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | Range of how many targets to check for                               | >0      |
| targeter  |           | If provided, this condition will check against the targets of the given targeter instead | <!--type:Targeter--> |


## Examples
```yaml
  Conditions:
  - targets{a=>0} true
```

```yaml
  Conditions:
  - targets{a=0to5} true
```

```yaml
  Conditions:
  - targets{a=>10;targeter=@MIR{r=10;type=SomeMythicMob}} true
```