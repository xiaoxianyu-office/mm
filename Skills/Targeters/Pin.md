## Description
Targets the location of a [Pin].
If the Pin is a Multi-Pin made via a Pin Wand, this targets all of the associated locations.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| name      | n, pin, p, key, k | The name of the [pin] to target                              |<!--type:Pin--> |
| random | r |Whether to select a single and random location, if the specified pin is a Multi-Pin| false |


## Examples
```yaml
  Skills:
  - teleport @Pin{p=mypin}
```


<!-- LINKS -->
[pin]: /Pins