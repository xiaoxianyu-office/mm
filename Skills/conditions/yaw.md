## Description
Checks the yaw of the target entity against a range.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| yaw       | y         | The yaw to check for                                                 | 0       |
| clamp     | c         | Whether to clamp yaw to a value in a 0-360 range                     | true    |

## Examples
```yaml
  Conditions:
  - yaw{y=90to180} true
```

```yaml
  Conditions:
  - yaw{y=>0} true
```