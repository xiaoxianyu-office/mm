## Description
Check if a [Pack](/wikis/Packs) with the specified id is present on the server with a version that is either greater or equal the specified one.


## Attributes
| Attribute | Alias       | Description                                                        | Default |
|-----------|-------------|--------------------------------------------------------------------|---------|
| packid    | pack, id, p | The Pack id to check for                                           |         |
| packversion | packV, version, v | The version to check for                                   |         |


## Examples
```yaml
  Conditions:
  - packversiongreater{p="ThePackId",v="1.2.3"} true
```


## Aliases
- [x] packversiongreater
- [x] packversionisgreater