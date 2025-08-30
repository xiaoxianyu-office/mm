## Description
Check if a [Pack](/Packs) with the specified id is present on the server.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| packid    | pack, id, p | The pack id to check for                                           |         |


## Examples
```yaml
  Conditions:
  - mythicpack{p="ThePackId"} true
```


## Aliases
- [x] pack
- [x] haspack