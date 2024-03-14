## Description
Sets the text component of target Text Display entity


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| text      | t         | The new text to be set                                               |         |


## Examples
```yaml
ExampleTextDisplayEntity:
  Type: TEXT_DISPLAY
  DisplayOptions:
    Text: I am but a humble example, nothing to see here
  Skills:
  - settextdisplay{text="MUHAHAHA! YOU FELL FOR MY TRICKERY!";delay=100} @self ~onSpawn
```


## Aliases
- [x] setText