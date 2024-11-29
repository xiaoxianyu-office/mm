## Description
Modifies the a scoreboard-objective value of the specified targeter(s).

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
| action    | a         | The operation to perform                                             | ADD<!--type:ScoreAction-->|
| value     | v         | The value to perform the operation with                              |         |

  
## Examples
This example will track how often and whom damaged
the casting mob in battle.
```yaml
  Skills:
  - modifytargetscore{objective=damagescore;action=add;value=1} @trigger ~onDamaged
```


## Aliases
- [x] mts


[^mod]: shorthand for "Modular Division"



<!--TAGS-->
<!--tag:Scoreboard-->
