## Description
Modifies the a scoreboard-objective value of the casting mob. The skill
is a no-target skill and will always affect the casting mob's score.
Works exactly like the ModifyMobScore-mechanic, but is only capable of
performing the **set**-action.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| objective | obj, o    | Specifies the scoreboard objectiv to be changed. If the objective doesn't exist it will automatically be created by the mechanic                                               |         |
| value     | v         | The value to perform the operation with                              |         |


## Examples
This will set the mob score to Zero on the objective "MyScore"
```yaml
ResetMyMobScore:
  Skills:
  - setmobscore{o=MyScore;v=0}
```


## Aliases
- [x] sms


<!--TAGS-->
<!--tag:Scoreboard-->
