## Description
Targets all blocks in a chunk relative to the inherited target(s)

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| noair     | na        | Whether air should not be targeted                                   | true    |
| onlyair   | oa        | Whether only air should be targeted                                  | false   |
| nearorigin| no        | Whether the targeter should also target the origin                   | false   |


## Examples
```yaml
  Skills:
  - effect:particles @BlocksInChunk
```


## Aliases
- [x] BIC