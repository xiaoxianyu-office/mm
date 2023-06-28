## Description
Sets the targeted display entity's transformations


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| action    | a         | The action to use. Can be `SET`, `ADD`, `MULTIPLY`, `DIVIDE`         | SET     |
| transformationtype | transformation, type, tt | The type of the transformation. Can be `TRANSLATION`, `SCALE`, `RIGHT_ROTATION`, `LEFT_ROTATION`                                                 | TRANSLATION |
| value     | val       | The value of the transformation                                      | 0,0,0   |


## Examples
```yaml
ExampleDisplayEntity:
  Type: block_display
  Skills:
  - displaytransformation{action=set;transformation=translation;value=0,0,1} @self ~onDamaged
```


## Aliases
- [x] settransformation
- [x] transformation