## Description
Modifies the mob's threat value towards the target. Requires the casting mob
have [Threat Tables](/Mobs/ThreatTables) enabled in order to have any effect.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of threat to give the target. Can be negative.            | 1       |
| mode      | m         | The [mode](#mode-attribute) of the operation                         | add<!--type:ThreatMode-->|


### Mode Attribute
| Mode      | Aliases   | Description                                                                    |
|-----------|-----------|--------------------------------------------------------------------------------|
| add       |           | Adds `amount` threat to the target entity                                      |
| remove    |           | Removes `amount` threat from the target entity                                 |
| multiply  |           | Multiplies the threat against the target entity by `amount`                    |
| divide    |           | Divides the threat against the target entity by `amount`                       |
| set       |           | Sets the threat against the target entity to `amount`                          |
| reset     | delete    | Remove all threat from the target entity                                       |
| forcetop  | force, top, topthreat, taunt | Gives the target enough threat to be moved to the top of the threat list |


## Examples
This example will set the nearest player's threat level to a very high
amount.
```yaml
Fixate:
  Skills:
  - threat{amount=10000} @NearestPlayer ~onSpawn
```


## Aliases
- [x] threatchange
- [x] threatmod


<!--TAGS-->
<!--tag:Threat-->
