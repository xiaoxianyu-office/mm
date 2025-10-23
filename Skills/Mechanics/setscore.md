## Description
Modifies the scoreboard-objective value of a fake player name. Works
like the [Modify Score](/skills/mechanics/modifyscore) mechanic, but is
only capable of performing the **set**-action.


## Attributes
> This mechanic inherits every *inheritable* attribute of the [ModifyScore](/Skills/Mechanics/modifyscore) mechanic
>> - The `action` attribute is **set** at `SET` and cannot be modified

  
## Examples
This example will set the score of a player named
"Bob" for the objective "TestScore", even if that player doesn't exist
on the server.  
It will create the objective if it does not currently exist.
```yaml
  Skills:
  - setscore{o=TestScore;e=Bob;v=1} ~onInteract 
```
![](https://i.imgur.com/0HKvAUM.png)


<!--TAGS-->
<!--tag:Scoreboard-->
