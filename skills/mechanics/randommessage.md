## Description
Sends a random message to the target player. Does nothing if the target
is not a player. No limit to how much messages can be added to the list.
The special character # will cause this skill to fail.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| messages  | m, message, msg, msgs | A list of message strings to send to the player, separated by commas. Each string must be in quotes. These strings can use variables.                        |         |


## Examples
This will each player n a 20 blocks radius one random message when the caster is interacted with.
```yaml
  Skills:
  - randommessage{
      m=
      "message 1",
      "message 2",
      "message 3";
      } @PIR{r=20} ~onInteract
```
##
This will do the same as above, but this time sending 2 random messages per each player
```yaml
  Skills:
  - randommessage{m="one test","not a test","test";repeat=1} @PIR{r=20} ~onInteract
```


## Aliases
- [x] randommsg
- [x] rm
- [x] rmsg


<!--TAGS-->
<!--tag:Random-->
<!--tag:Message-->