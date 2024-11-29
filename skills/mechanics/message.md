## Description
Sends a chat message to the target, if the target is a player. [Color
codes](/Skills/Placeholders#color-codes) and
[variables](/Skills/Variables) are useable in this mechanic.

* Allows hex colors in the format **`<#FFFFFF>`**
* Supports gradients in the format **`<gradient:#color1:#color2>text</gradient>`**
* Supports **`<rainbow>text</rainbow>`**
* Supports hover text in the format **`<hover:show_text:'hover text??'>hover over me!</hover>`**
* Supports clickable text in the format **`<click:run_command:/say hello>click me!</click>`**


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| message   | msg,m     | The message to send                                                  | None    |
| audience  |           | the [audience] of the message                                        | <!--type:Audience-->|


## Examples
```yaml
   Skills:
   - message{m="<caster.name>&f<&co> Hahaha! You will all die!"} @PlayersInRadius{r=30}
```


## Aliases
- [x] m
- [x] msg


<!-- LINKS -->
[audience]:/Skills/Audience


<!--TAGS-->
<!--tag:Message-->