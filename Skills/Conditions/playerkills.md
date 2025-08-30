## Description
Matches how many players the target mob has killed.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| kills     | k         | The number range to match                                            | 0       |


## Examples

```yaml
  Conditions:
  - playerkills{k=>10} true
```