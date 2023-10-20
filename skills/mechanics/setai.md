================

## Description:

Toggles the target AI

## Attributes:

| Attribute | Aliases | Description                  | Default Value |
|-----------|---------|------------------------------|---------------|
| ai        |         | Sets the new mob AI, boolean |               |

## Examples:

```yaml
TemporaryAISwitcher:
  Skills:
    - setAI{ai=false} @self
    - delay 100
    - setAI{ai=true} @self
```