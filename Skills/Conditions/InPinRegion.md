## Description
Checks if the target entity is within a region delimited by two [pins].


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| pin1      | p1        | The first [pin]                                                      |         |
| pin2      | p2        | The second [pin]                                                     |         |


## Examples
```yaml
  TargetConditions:
  - inpinregion{p1=mypin;p2=anotherpin}
```


<!-- LINKS -->
[pin]: Pins
[pins]: Pins