## Description
Tests the sky light level at the target location. This is the light coming from the sky only, unlike `lightlevel` (total light) or `lightlevelfromblocks` (block light).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| level     | l         | The sky light level range to match                                   | 0       |


## Examples
```yaml
  Conditions:
  - skylightlevel{l=10} true
```

```yaml
  Conditions:
  - skylightlevel{l=>10} true
```

```yaml
  Conditions:
  - skylightlevel{l=1to10} true
```
