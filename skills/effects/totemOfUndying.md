## Description
Plays the effect of a totem resurrecting a player with options to specify CustomModelData to use from resource packs.

*Note: You can't disable the sound that plays*

## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| model     |           | The CustomModelData to use.                                          |         |

## Examples

```yaml
PlayTotemEffect:
  Skills:
  - totemofundying{model=2} @PIR{r=5}
```

## Aliases
- [X] totemeffect
- [X] totemundying
- [X] totemresurrection