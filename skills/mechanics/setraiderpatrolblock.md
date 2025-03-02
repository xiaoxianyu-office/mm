## Description
Sets the target raider to patrol the given location


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| location  |block, l, b| A [Location Targeter], whose targeted location will be the specified one |<!--type:Targeter-->|                                       


## Examples
```yaml
  Skills:
  - setRaiderPatrolBlock{l=@TrackedLocation} @self
```

## Aliases
- [x] setRaiderBlock

[Location Targeter]: /Skills/Targeters#single-location-targeters