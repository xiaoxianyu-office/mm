Every [pack] now allows for a `pins.yml` file. This file can contain a list of locations that will be handled in a special way by mm: they will be considered "pins", enabling them to be targeted or checked against with more ease.


## Commands
| Command | Permission | Description |
| ------- | ---------- | ----------- |
| `/mm pins create [pack] [name]`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | Allows you to save your current location as a pin named `[name]` inside the `[pack]` pack                                                                                                                                                                          |
| `/mm pins list`                                                                                                                                                                          | mythicmobs.command.pins.list                                                                                                                                                                          | Lists all the active pins                                                                                                                                                                          |
| `/mm pins move [name]`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | Moves the pin named `[name]` to the current location                                                                                                                                                                          |
| `/mm pins remove [pack] [name]`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | Removes the pin named `[name]` from the `[pack]` pack                                                                                                                                                                          |
| `/mm pins toggleviewing`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | Shows where each pin is via a text display entity                                                                                                                                                                          |


## Targeters
- [Pin Targeter](Skills/Targeters/Pin)


## Conditions
- [inPinRegion Condition](Skills/Conditions/InPinRegion)


<!-- LINKS -->
[pack]: Packs