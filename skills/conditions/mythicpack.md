**Description**: check if a [Pack](/wikis/Packs) with the specified id is present on the server.

## Attributes
| Attribute | Alias       | Description                                                        | Default |
|-----------|-------------|--------------------------------------------------------------------|---------|
| packid    | pack, id, p | The Pack id to check for                                           | none    |

## Examples
```yaml
  Conditions:
  - mythicpack{p="ThePackId"} true
```