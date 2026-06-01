## Description
Applies an aura to the targeted entity that triggers a skill when the player releases a specific key.

The key is identified by an [AriKeys](https://www.spigotmc.org/resources/arikeys.97150/) key ID, so the AriKeys plugin must be installed for this mechanic to function. While the aura is active, releasing the bound key on the affected player runs the `onRelease` skill.

> This mechanic requires the [AriKeys](https://www.spigotmc.org/resources/arikeys.97150/) plugin to be installed.


## Attributes
| Attribute | Aliases | Description                                          | Default |
|-----------|---------|------------------------------------------------------|---------|
| onRelease | or      | The skill to trigger when the key is released        |         |
| key       | k       | The key ID that triggers the skill                   |         |

> This mechanic inherits every *inheritable* attribute of the [aura](/Skills/Mechanics/aura) mechanic


## Examples
Applies an aura that casts the `ChargeRelease` skill when the player releases the bound key, for 10 seconds.
```yaml
  Skills:
  - onKeyRelease{key=keybind.charge;onRelease=ChargeRelease;duration=200} @trigger
```


## Aliases

- [x] keyRelease
- [x] kr
