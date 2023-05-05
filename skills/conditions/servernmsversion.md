**Description**: Checks is the server is running a specific minecraft NMS version

## Attributes
| Attribute | Alias       | Description                                                        | Default |
|-----------|-------------|--------------------------------------------------------------------|---------|
| v         |             | The version to check for                                           |         |

## Examples
```yaml
  Conditions:
  - nmsversion{v="v1_19_R1"}
```

## Aliases
  - [x] servernms
  - [x] nmsversion