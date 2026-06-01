## Description
Applies an aura to the targeted entity that triggers a skill when the player presses a specific key.

The key is identified by an [AriKeys](https://www.spigotmc.org/resources/arikeys.97150/) key ID, so the AriKeys plugin must be installed for this mechanic to function. While the aura is active, pressing the bound key on the affected player runs the `onPress` skill.

> This mechanic requires the [AriKeys](https://www.spigotmc.org/resources/arikeys.97150/) plugin to be installed.


## Attributes
| Attribute | Aliases | Description                                          | Default |
|-----------|---------|------------------------------------------------------|---------|
| onPress   | op      | The skill to trigger when the key is pressed         |         |
| key       | k       | The key ID that triggers the skill                   |         |

> This mechanic inherits every *inheritable* attribute of the [aura](/Skills/Mechanics/aura) mechanic


## Examples
Applies an aura to the player that casts the `Dash` skill whenever they press the bound key, for 10 seconds.
```yaml
  Skills:
  - onKeyPress{key=keybind.dash;onPress=Dash;duration=200} @trigger
```


## Aliases

- [x] keyPress
- [x] kp
