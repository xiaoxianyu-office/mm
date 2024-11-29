## Description
Modifies the scoreboard-objective value of the casting mob.
Does not support targeters.

## Attributes
> This mechanic inherits every attribute of the [ModifyGlobalScore](/Skills/Mechanics/modifyglobalscore) mechanic

  
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


## Aliases
- [x] mms


<!--TAGS-->
<!--tag:Scoreboard-->
