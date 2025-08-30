## Description
Checks if the target location is near any claims of any supported plugins.  

Supported Plugins:

- GriefPrevention
- Lands
- CrashClaim


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The given range to check                                             | 16      |


## Example
```yaml
  Conditions:
  - nearclaim{r=20} false
```


## Aliases
- [x] nearClaims