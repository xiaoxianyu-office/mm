## Description
Checks if the [@origin] is within a certain distance of a specified [pin]


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| pin       | p         | The pin to check against                                             |<!--type:Pin--> |
| distance  | d         | The distance to check against. Can be a range.                       |         |


## Examples
```yaml
  Conditions:
  - originDistanceFromPin{pin=example_pin;d=>10} true
```


<!-- LINKS -->
[pin]: /Pins
[@origin]: /Skills/Targeters/Origin