## Description
Check if a [Pack](/Packs) with the specified id is present on the server with the specified version.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| packid    | pack, id, p | The Pack id to check for                                           |         |
| packversion | packV, version, v | The version to check for                                   |         |


## Examples
```yaml
  Conditions:
  - packversion{p="ThePackId",v="1.2.3"} true
```


## Aliases
- [x] packversion
- [x] packversionis