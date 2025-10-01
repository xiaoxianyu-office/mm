## Description
Modifies the scoreboard-objective value of a fake player name.  
Can also be used to modify a specific players score.

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
| objective   | obj, o  | Specifies the scoreboard objective to be changed. If the objective doesn't exist it will automatically be created by the mechanic                                               |         |
| action      | a       | The operation to perform                                             | SET<!--type:ScoreAction-->|
| value       | v       | The value to perform the operation with                              | 0       |
| name, entry | n, e    | The name of the player/fake player                                   | dummy   |


## Examples
This example will add one to the score of a player
named "Bob" for the objective "TestScore", even if that player doesn't
exist on the server.  
It will create the objective if it does not currently exist.
```yaml
  Skills:
  - modifyscore{o=TestScore;e=Bob;a=add;v=1} ~onInteract 
```
![](https://i.imgur.com/0HKvAUM.png)

[^mod]: shorthand for "Modular Division"


<!--TAGS-->
<!--tag:Scoreboard-->
