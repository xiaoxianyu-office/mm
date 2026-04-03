## Description
Shows a [Dialog](/Dialogs) to the target player. Dialogs are interactive UI windows built with the Paper Dialog API that can display text, items, inputs, and buttons.

Dialog definitions are configured in YAML files inside the `Dialogs/` folder. See the [Dialogs](/Dialogs) page for full configuration details.

> **This is a [Paper-Only] mechanic!**

> **This is a [Premium-Only] mechanic!**

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.dialog.button>`    |
| `<skill.var.dialog.<key>>`     |

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| dialog    | d, name   | The name of the dialog definition to show                            | default |


### Dialog Attribute
The name must match a dialog defined in a YAML file inside your `Dialogs/` folder. Supports placeholders.


## Response Variables
When a player clicks a button in the dialog, the associated skill is executed with the following variables injected into the skill metadata:

| Variable | Description |
|----------|-------------|
| `dialog.button` | The index of the clicked button (integer, starting at 0) |
| `dialog.<key>` | The value of each visible input, where `<key>` is the input's `Key` field |

Input values are typed based on the input type:
- **text** / **option** — string
- **bool** — `true` or `false`
- **range** — float value (e.g. `5.0`)


## Examples
Shows a simple welcome notice to the player that interacted with the mob.
```yaml
  Skills:
  - showDialog{dialog=WelcomeNotice} @trigger
```
##
Shows a quest offer dialog using a placeholder for the dialog name.
```yaml
  Skills:
  - showDialog{d=QuestOffer} @trigger
```
##
Shows a character setup dialog to all players within 10 blocks.
```yaml
  Skills:
  - showDialog{d=CharacterSetup} @PlayersInRadius{r=10}
```


## Aliases
- [x] openDialog
- [x] dialog


<!-- LINKS -->
[Paper-Only]: https://papermc.io/downloads/all
[Premium-Only]: Premium-Features
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders
