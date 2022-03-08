Goal: crossbowAttack
--------------

Attack with a crossbow. Only Piglins and Pillagers can use crossbowAttack goal as long as they're holding a crossbow.

### Attributes

| Attribute      | Aliases  | Description                        | Default |
|----------------|----------|------------------------------------|:-------:|
| speed          | s        | Movement speed modifier            |    1    |
| attackradius   | radius,r | The attack radius of this ai goal. |    8    |


### Examples

```yaml
ExampleMob:
  Type: Piglins
  Equipment:
    - crossbow HAND
  AIGoalSelectors:
    - clear
    - crossbowAttack{speed=1;radius=15}
```