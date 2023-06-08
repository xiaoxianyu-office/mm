## Description
Adds an attribute modifier to the attributable target


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| attribute | attr      | The attribute                                                   | GENERIC_LUCK |
| operation | op        | The operation to perform                                          | ADD_NUMBER |
| amount    | amt, a    | The modifier of the attribute                                          | 0     |
| duration  | dur       | The duration of the attribute                                          | 0     |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  Skills:
  - attributeModifier{attribute=GENERICK_LUCK;a=2;d=1200;op=ADD_NUMBER} @trigger ~onDeath
```