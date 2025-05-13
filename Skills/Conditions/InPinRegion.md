## Description
Checks if the target location is within a region delimited by two [pins].


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| pin1      | p1        | The first [pin]                                                      |<!--type:Pin--> |
| pin2      | p2        | The second [pin]                                                     |<!--type:Pin--> |


## Examples
```yaml
  TargetConditions:
  - inpinregion{p1=mypin;p2=anotherpin}
```


<!-- LINKS -->
[pin]: /Pins
[pins]: /Pins