## Description
Applies an [aura] on the target player that triggers a [metaskill] when they type a chat message

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.input>`            |

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onChatSkill | onchat, oc, then  | The [metaskill] to execute when the player chats           |<!--type:Metaskill-->|

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
This below example uses the [StringEquals](/skills/conditions/stringequals) condition to check what the player typed! The message mechanic will only appear if the player typed `QueenOfAnts is a noob`.
```yaml
YourMob:
  Type: ZOMBIE
  Skills:
  - onChat{onChat=ChatSkill;d=1000} @trigger ~onInteract

ChatSkill:
  Conditions:
  - stringequals{val1="<skill.var.input>";val2="QueenOfAnts is a noob"} true
  Skills:
  - message{m=She is indeed!} @trigger
```

## Aliases
- [x] chatprompt


<!-- LINKS -->
[metaskill]: /Skills/Metaskills
[aura]: /skills/mechanics/aura
[skill-scoped variable]: /Skills/Variables
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
