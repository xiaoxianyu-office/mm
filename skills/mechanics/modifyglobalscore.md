## Description
Modifies the scoreboard-objective value of the fake player `__GLOBAL__`.
This is a notarget skill and cannot affect any other players' score.

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
| action    | a         | The operation to perform                                             | ADD<!--type:ScoreAction--> |
| value     | v         | The value to perform the operation with                              |         |

  
## Examples
```yaml
  Skills:
  - modifyglobalscore{objective=someobjective;action=multiply;v=2} ~onAttack
```


## Aliases
- [x] mgs


[^mod]: shorthand for "Modular Division"


<!--TAGS-->
<!--tag:Scoreboard-->
