## Description
Pushes a button at the supplied coordinates.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| x         |           | The X coordinate of the button                                       | 0       |
| y         |           | The Y coordinate of the button                                       | 0       |
| z         |           | The Z coordinate of the button                                       | 0       |
| location  | loc, l    | Location of the action, in a `x,y,z` syntax. If set, other attributes are ignored     |           |


## Examples
```yaml
HitSecretButton:
  Skills:
  - pushbutton{x=15;y=67;z=-213}
```


## Aliases
- [x] buttonpush


<!--TAGS-->
<!--tag:World-->