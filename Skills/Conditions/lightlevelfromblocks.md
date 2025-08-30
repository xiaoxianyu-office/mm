## Description
Tests the light level originating from light-emitting blocks at the target location


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| level     | l         | The light level range to match                                       | 0       |


## Examples
```yaml
  Conditions:
  - lightlevelfromblocks{l=10} true
```

```yaml
  Conditions:
  - lightlevelfromblocks{l=>10} true
```

```yaml
  Conditions:
  - lightlevelfromblocks{l=1to10} true
```

## Aliases
- [x] blocklightlevel