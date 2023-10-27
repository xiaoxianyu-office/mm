## Description
Sets the size of the target `INTERACTION` [Type](/mythiccraft/MythicMobs/-/wikis/Mobs/Mobs#type) entity.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| height    | h         | The value to set the height to                                       | 1       |
| width     | w         | The value to set the width to                                        | 1       |


## Examples
The following would set the size of the casting interaction entity to a 2x3 when right clicked
```yaml
ExampleInteractionEntity:
  Type: INTERACTION
  Skills:
  - setInteractionSize{height=2;width=3} @self ~onInteract
```


## Aliases
- [x] interactionSize