## Description
Checks whether the server is after or equal to a specific version


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| version | v, sv | The version to check against | 1.19.3 |
| inclusive | i | Whether the condition should check if the current version is exactly the specified one | true |


## Examples
```yaml
  Conditions:
  - serverAfter{version=1.21.1} false
  Skills:
  - message{m="Ngl y'all gotta update"} @world
```


## Aliases
- [x] serverAfterEq
- [x] serverAfter
- [x] versionAfterEq
- [x] versionAfter