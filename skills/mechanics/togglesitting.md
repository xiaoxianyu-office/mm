## Description
Toggles the sitting state for cats, dogs, foxes, and parrots.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| setSitting| state     | Sets the sitting state                                               | false   |


## Examples
Makes the wolf sit when right clicked.
```yaml
ExampleDog:
  Type: Wolf
  Skills:
  - sit{state=true} @Self ~onInteract
```

## Aliases: 
- [x] sit


<!--TAGS-->
<!--tag:AI-->
