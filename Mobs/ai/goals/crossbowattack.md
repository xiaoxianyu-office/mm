## Description
Attack with a crossbow. Only Piglins and Pillagers can use crossbowAttack goal as long as they're holding a crossbow.


### Attributes
> *This aigoal has no attributes*

### Examples

```yaml
ExampleMob:
  Type: Piglins
  Equipment:
    - crossbow HAND
  AIGoalSelectors:
    - clear
    - crossbowAttack
```