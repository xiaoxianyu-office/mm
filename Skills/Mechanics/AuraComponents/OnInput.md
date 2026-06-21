## Description
Triggers a skill on player input. The component can require directional movement, jump/sneak/sprint states, or any movement. Matched states are exported as integer variables


| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.input-forward>`    |
| `<skill.var.input-backward>`    |
| `<skill.var.input-right>`    |
| `<skill.var.input-left>`    |
| `<skill.var.input-jump>`    |
| `<skill.var.input-sneak>`    |
| `<skill.var.input-sprint>`    |

> [!important] Variable's values
> The values of those variables are either `0` if the input is not being currently used or `1` if it is

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| oninputskill | oninput, oi | Skill executed on matching input state |<!--type:MetaSkill-->|
| forward |  | Whether forward input is required | false |
| backward |  | Whether backward input is required | false |
| left |  | Whether left input is required | false |
| right |  | Whether right input is required | false |
| requireanymovement | anymovement, move | Whether any directional input is required | false |
| requirejump | jump | Whether jump input is required | false |
| requiresneak | sneak | Whether sneak input is required | false |
| requiresprint | sprint | Whether sprint input is required | false |



## Aliases
- [x] playerinput


<!-- LINKS -->
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders
