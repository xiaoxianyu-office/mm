## Description
Sets the sitting state of the target wolf.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| state     | sit, value | The state the wolf is in. True = sitting and False = standing       |         |


## Examples
```yaml
# Standing
- wolfSit{state=false} @self ~onInteract
```

```yaml
# Sitting
- wolfSit{state=true} @self ~onInteract
```