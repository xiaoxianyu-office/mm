## Description
Targets a nearby safe escape location like how an Enderman would choose its teleport destination


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The maximum horizontal and vertical offset from the caster used when randomly searching for a teleport destination | 32|
| iterations | i        | How many times the plugin will try to find a suitable teleport destination  | 64|
| height    | h         | The number of vertical air blocks required at the destination to ensure the entity fits safely | 3|


## Examples
```yaml
  Skills:
  - teleport @escapelocation{radius=32;iterations=64;height=3}
```


## Aliases
- [x] EndermanTeleport