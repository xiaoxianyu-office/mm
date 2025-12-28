## Description
Targets a nearby safe escape location like how an Enderman would choose its teleport destination


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius from the caster in which the teleport destination may be located | 32|
| iterations | i        | How many times the plugin will try to find a suitable teleport destination  | 64|
| height    | h         | The maximum height different between the caster and the teleport destination | 3|


## Examples
```yaml
  Skills:
  - teleport @escapelocation{radius=32;iterations=64;height=3}
```


## Aliases
- [x] EndermanTeleport
- [ ] 