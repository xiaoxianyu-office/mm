## Description
Checks whether the damage that caused the current skill tree has a specific tag


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| tag       | t         | The tag to check against                                             |         |
| value     | val, v, b, bool, boolean | If true, checks for the presence of the tag<br>If false, checks for its absence | true  |


## Examples
```yaml
Conditions:
- damageTag{tag=WITCHCURSES}
```
Used to check the damage tag specified in the [Damage](/skills/mechanics/damage) mechanic or mechanics inheriting its attributes


## Aliases
- [x] damagehastag