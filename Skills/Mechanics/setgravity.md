## Description
Sets whether gravity affects the target entity.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| gravity   | g, b, bool, u, use | Sets whether the entity uses gravity                        | true    |

  
## Examples
```yaml
  Skills:
  - setgravity{g=false} @self ~onSpawn
  - setusegravity{g=false} @self ~onSpawn
  - ...
```


## Aliases
- [x] setusegravity