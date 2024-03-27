Every [pack] now allows for a `pins.yml` file. This file can contain a list of locations that will be handled in a special way by mm: they will be considered "pins", enabling them to be targeted or checked against with more ease.


## Commands
| Command | Permission | Description |
| ------- | ---------- | ----------- |
| `/mm pins create [pack] [name]`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | Allows you to save your current location as a pin named `[name]` inside the `[pack]` pack                                                                                                                                                                          |
| `/mm pins list`                                                                                                                                                                          | mythicmobs.command.pins.list                                                                                                                                                                          | Lists all the active pins                                                                                                                                                                          |
| `/mm pins move [name]`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | Moves the pin named `[name]` to the current location                                                                                                                                                                          |
| `/mm pins remove [pack] [name]`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | Removes the pin named `[name]` from the `[pack]` pack                                                                                                                                                                          |
| `/mm pins toggleviewing`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | Shows where each pin is via a text display entity                                                                                                                                                                          |
| `/mm pins wand [pack] [pinName]`                                                                                                                                                                          | mythicmobs.command.pins                                                                                                                                                                          | While holding a pin wand, left-clicking will create the multi-pin and points to it and right-clicking will remove the most recent point from a multi-pin                                                                                                                                                                          |


## Targeters
- [@Pin](/Skills/Targeters/Pin)


## Conditions
- [inPinRegion](/Skills/Conditions/InPinRegion)
- [DistanceFromPin](/skills/conditions/DistanceFromPin)

<!-- LINKS -->
[pack]: Packs