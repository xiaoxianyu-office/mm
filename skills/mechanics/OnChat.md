## Description
Applies an [aura] on the target player that triggers a [metaskill] when they type a chat message


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onChatSkill | onchat, oc, then  | The [metaskill] to execute when the player chats           |         |

> This mechanic inherits every attribute of the [aura] mechanic

## onChatSkill Attribute
When the metaskill is execute, a new [skill-scoped variable] containing what has been said in chat is set, called `input`.  
Its value can then be fetched via the `<skill.var.input>` placeholder.


## Examples
The `ExampleSkill` metaskill will create an aura on every player in a 20 blocks radius. If those players were to chat during its 10 seconds duration, a message would be sent to them and they would be set on fire.
```yaml
ExampleSkill:
  Skills:
  - onChat{onChat=ExampleSkill2;d=200} @PIR{r=20}

ExampleSkill2:
  Skills:
  - message{m="SILENCE!"} @trigger
  - ignite @trigger
```


## Aliases
- [x] chatprompt


[metaskill]: /Skills/Metaskills
[aura]: /skills/mechanics/aura
[skill-scoped variable]: /Skills/Variables