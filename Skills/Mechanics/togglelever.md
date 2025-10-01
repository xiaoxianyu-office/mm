## Description
Toggles a lever on and off at the supplied coordinates.

The lever will switch back to the starting position after a set amount
of time. (Defaulting to 20 ticks/1 second).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| location  | loc, l    | Location of the action, in a `x,y,z` syntax. If set, other location attributes are ignored |           |
| duration  | d         | The duration (in ticks) the lever should remain toggled on.          | 20      |
| x         |           | The X coordinate of the button.                                      | 0       |
| y         |           | The Y coordinate of the button.                                      | 0       |
| z         |           | The Z coordinate of the button.                                      | 0       |

  
## Examples
Toggles a lever placed at the given coordinates.
```yaml
OpenSecretDoor:
  Skills:
    - togglelever{duration=600;x=15;y=67;z=-213}
```


## Aliases
- [x] lever


<!--TAGS-->
<!--tag:World-->
