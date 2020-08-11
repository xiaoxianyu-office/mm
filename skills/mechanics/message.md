Mechanic: Message
=================

Sends a chat message to the target, if the target is a player. [Color
codes](/databases/misc/colorcodes) and
[variables](/skills/stringvariables) are useable in this mechanic.

Attributes
----------

| Attribute | Aliases | Description          | Default |
|-----------|---------|----------------------|---------|
| message   | msg,m   | The message to send. | None    |

  

Examples
--------

      Skills:
      - message{m="<mob.name>&f<&co> Hahaha! You will all die!"} @PlayersInRadius{r=30}
