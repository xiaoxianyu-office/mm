## Description
Makes the player fly, similar to the /fly command. Can use any aura
attribute.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| duration  | d         | Duration of the aura                                                 | 200     |

  
## Examples
```yaml
  Skills:
  - fly{duration=100} @trigger ~onInteract
```