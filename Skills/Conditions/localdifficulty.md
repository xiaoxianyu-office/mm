## Description
Tests the difficulty scale at the target location.
 

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| difficulty| diff, d   | The difficulty range to check                                        |         |

 
## Examples
```yaml
  Conditions:
  - localdifficulty{d=>0}
```