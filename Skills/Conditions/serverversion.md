## Description
Checks is the server is running a specific minecraft version


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| version   | sv, v       | The version to check for                                           | 1.19.3  |


## Examples
```yaml
  Conditions:
  - serverversion{v="v1.19.4"} true
```


## Aliases
- [x] server
- [x] version