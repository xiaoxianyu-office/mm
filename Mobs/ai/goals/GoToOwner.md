## Description
Makes the mob move towards its [owner](/Skills/Targeters/Owner) when beyond a certain distance.  
[Followrange](/Mobs/Options#followrange) must be more than the distance between the owner and the mob)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| followrange | fr, r, maxrange | Distance after which the mob will start to follow the owner  | 4       |
| minrange  | mr        | Distance in which the mob will stop following the owner              | 4       |
| speed     | s         | Speed of the movement                                                | 1.0     |
| droptarget | dt       | Whether the current target should be dropped when the mob starts following the owner  | true |
| teleportToWorld | ttw, tow | Whether the mob will teleport if the owner is in a different world | true |

## Examples
```yaml
  AIGoalSelectors:
  - clear
  - gotoowner{fr=10;mr=3}
```