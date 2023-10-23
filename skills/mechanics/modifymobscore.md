## Description
Modifies the scoreboard-objective value of the casting mob.
Does not support targeters.

A list of possible operations for the action-syntax:

-   `SET`
-   `ADD`
-   `SUBTRACT`
-   `MULTIPLY`
-   `DIVIDE`
-   `MOD` [^mod]


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| objective | obj, o    | Specifies the scoreboard objectiv to be changed. If the objective doesn't exist it will automatically be created by the mechanic                                               |         |
| action    | a         | The operation to perform                                             | ADD     |
| value     | v         | The value to perform the operation with                              |         |

  
## Examples
```yaml
  Skills:
  - modifymobscore
      {
      objective=someobjective;
      action=multiply;
      v=2
      } ~onAttack
```
[^mod]: shorthand for "Modular Division"