## Description
Sends a message to the target player's action bar.

[Color codes](/Skills/Placeholders#color-codes) and
[Variables](/Skills/Variables) are compatible with the action
message bar. Some targeters might not work properly with this mechanic.
If you happen to find a targeter that doesn't work, please be sure to
post it in the bugs/suggestion-subforum!

![](http://fs5.directupload.net/images/160306/zswobuo8.jpg)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| message   | m, msg    | The message to send. Must be surrounded by quotes                    |         |


## Examples
```yaml
  Skills:
  - actionmessage{m="<caster.name>&f is casting a spell!"} @PlayersInRadius{r=30}
  - actionmessage{m="&lHello! &cI'm &athe &9&lactionmessage-bar&r! &e:)"} @trigger
  - am{m="<caster.name>&f is using the *skill alias!*"} @PlayersInRadius{r=30}
```


## Aliases
- [x] am
- [x] actionmessage


<!--TAGS-->
<!--tag:Message-->
