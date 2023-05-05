**Description**: Checks is the server is running a specific minecraft version

## Attributes
| Attribute | Alias       | Description                                                        | Default |
|-----------|-------------|--------------------------------------------------------------------|---------|
| v         |             | The version to check for                                           |         |

## Examples
```yaml
  Conditions:
  - serverversion{v="v1.19.4"} true
```

## Aliases
  - [x] server
  - [x] version