## Description
Sets the target's yaw and pitch to the same value of the specified target attribute


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| target    | to, t, location, loc, l, of | The [targeter](/Skills/Targeters)                  |<!--type:Targeter-->|


## Examples
```yaml
  Skills:
  - matchrotation{target=@Parent} @self
```


## Aliases
- [x] matchrot


<!--TAGS-->
<!--tag:Movement:Rotation-->
