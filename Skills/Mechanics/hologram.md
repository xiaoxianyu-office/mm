## Description
Spawns a hologram at a target location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
|    text   | t         | The text to show                                       | Hologram Text Missing |
|    stay   | time, staytime  | The duration of the hologram in ticks                          | 100     |


## Examples
Creates a hologram above the mob when the mob gets right clicked, which displays for 100 ticks.
```yaml
  Skills:
  - holo{text="Example Text";time=100} @selflocation{y=1.6} ~onInteract
```

## Aliases
- [x] summonhologram
- [x] holo