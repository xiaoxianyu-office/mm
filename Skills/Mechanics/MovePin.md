## Description
Moves the given [pin](/Pins) to the target location.  
Cannot move MultiPins.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| pin       | p         | The pin to move                                                      |<!--type:Pin--> |


## Examples
```yaml
  Skills:
  - movepin{pin=example} @selflocation
```
> Moves the pin named "example" to the current location of the caster


<!--TAGS-->
<!--tag:Pin-->