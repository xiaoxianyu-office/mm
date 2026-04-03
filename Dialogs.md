Dialogs allow you to show interactive UI windows to players using the [Paper Dialog API]. This is a **[Premium Feature]** and requires **Paper 1.21.6+**.

Show dialogs to players using the [showDialog](/Skills/Mechanics/ShowDialog) mechanic, or with the `/mm dialogs show` command.

All text fields support [MiniMessage](https://docs.advntr.dev/minimessage/format.html) formatting and MythicMobs [placeholders](/Skills/Placeholders).

[[_TOC_]]

## Configuration
Dialog files are placed in the `Dialogs/` folder inside your MythicMobs pack. Filenames must contain `dialog` (e.g. `ExampleDialogs.yml`, `quest-dialog.yml`).

```yaml
DialogName:
  Title: "<gold>Dialog Title"
  ExternalTitle: "Short Title"
  CanClose: true
  Pause: false
  AfterAction: CLOSE
  Columns: 1
  Body:
  - Type: text
    Message: "<gray>Some text here."
    Width: 256
    Conditions:
    - condition1
  - Type: item
    Item: DIAMOND_SWORD
    Width: 64
    Height: 64
    Decoration: true
    ShowTooltip: true
  Inputs:
  - Type: text
    Key: myInput
    Label: "Enter something"
    MaxLength: 256
    Multiline: false
    Width: 200
    LabelVisible: true
  Buttons:
  - Label: "<green>Confirm"
    Tooltip: "Click to confirm"
    Width: 150
    Skill: SomeSkill
    Conditions:
    - condition1
  ExitButton:
    Label: "Close"
    Width: 100
    Skill: OptionalSkill
```


## Dialog Options

### Title
The main title displayed at the top of the dialog. Supports MiniMessage formatting and placeholders.
```yaml
  Title: "<gold>Welcome, <target.name>!"
```

### ExternalTitle
An optional shorter title used for external display purposes.
```yaml
  ExternalTitle: "Welcome"
```

### CanClose
Whether the player can close the dialog by pressing ESC.  
Defaults to `true`.
```yaml
  CanClose: false
```

### Pause
Whether the dialog should pause the game state while open.  
Defaults to `false`.
```yaml
  Pause: true
```

### AfterAction
Controls what happens after a button is clicked.

| Value | Description |
|-------|-------------|
| `CLOSE` | Closes the dialog after a button click |
| `NONE` | Does nothing after a button click |
| `WAIT_FOR_RESPONSE` | Keeps the dialog open until a response is given |

Defaults to `CLOSE`.
```yaml
  AfterAction: WAIT_FOR_RESPONSE
```

### Columns
The number of columns used to arrange buttons in multi-action dialogs (3+ buttons).  
Defaults to `1`.
```yaml
  Columns: 2
```


## Body Elements
The `Body` section defines the visual content of the dialog. Each element can be either text or an item display.

### Text Element
Displays formatted text in the dialog.

| Field | Description | Default |
|-------|-------------|---------|
| `Type` | Must be `text` | |
| `Message` | Text content (MiniMessage + placeholders) | |
| `Width` | Pixel width of the text area (max 1024) | 256 |
| `Conditions` | Optional list of [conditions](/Skills/Conditions) for visibility | |

```yaml
  Body:
  - Type: text
    Message: "<gray>A mysterious stranger needs your help."
    Width: 300
```

### Item Element
Displays a Minecraft item in the dialog.

| Field | Description | Default |
|-------|-------------|---------|
| `Type` | Must be `item` | |
| `Item` | Minecraft material name (e.g. `DIAMOND_SWORD`) | |
| `Width` | Display width in pixels (max 256) | 64 |
| `Height` | Display height in pixels (max 256) | 64 |
| `Decoration` | Whether to show item frame decorations | `false` |
| `ShowTooltip` | Whether to show the item tooltip on hover | `false` |
| `Conditions` | Optional list of [conditions](/Skills/Conditions) for visibility | |

```yaml
  Body:
  - Type: item
    Item: DIAMOND_SWORD
    Width: 64
    Height: 64
    Decoration: true
    ShowTooltip: true
```


## Inputs
The `Inputs` section defines interactive input fields. Player responses are stored as variables accessible via `dialog.<key>` in the skill triggered by the button.

### Text Input
A single or multi-line text field.

| Field | Description | Default |
|-------|-------------|---------|
| `Type` | Must be `text` | |
| `Key` | Variable name for the response | |
| `Label` | Display label | |
| `Width` | Input width in pixels (max 1024) | 200 |
| `LabelVisible` | Whether to show the label | `true` |
| `MaxLength` | Maximum character length | 256 |
| `Multiline` | Whether the input is multi-line | `false` |
| `Conditions` | Optional visibility [conditions](/Skills/Conditions) | |

```yaml
  Inputs:
  - Type: text
    Key: nickname
    Label: "Display Name"
    MaxLength: 16
```

### Bool Input
A checkbox toggle.

| Field | Description | Default |
|-------|-------------|---------|
| `Type` | Must be `bool` | |
| `Key` | Variable name for the response | |
| `Label` | Display label | |
| `Width` | Input width in pixels (max 1024) | 200 |
| `LabelVisible` | Whether to show the label | `true` |
| `Conditions` | Optional visibility [conditions](/Skills/Conditions) | |

```yaml
  Inputs:
  - Type: bool
    Key: pvpEnabled
    Label: "Enable PvP?"
```

### Range Input
A numeric slider.

| Field | Description | Default |
|-------|-------------|---------|
| `Type` | Must be `range` | |
| `Key` | Variable name for the response | |
| `Label` | Display label | |
| `Width` | Input width in pixels (max 1024) | 200 |
| `LabelVisible` | Whether to show the label | `true` |
| `Start` | Minimum value | |
| `End` | Maximum value | |
| `Initial` | Default value | |
| `Step` | Increment step size | |
| `LabelFormat` | Format string for the value display (e.g. `"%.0f"`) | |
| `Conditions` | Optional visibility [conditions](/Skills/Conditions) | |

```yaml
  Inputs:
  - Type: range
    Key: difficulty
    Label: "Difficulty"
    Start: 1
    End: 10
    Initial: 5
    Step: 1
    LabelFormat: "%.0f"
```

### Option Input
A dropdown selection.

| Field | Description | Default |
|-------|-------------|---------|
| `Type` | Must be `option` | |
| `Key` | Variable name for the response | |
| `Label` | Display label | |
| `Width` | Input width in pixels (max 1024) | 200 |
| `LabelVisible` | Whether to show the label | `true` |
| `Options` | Map of `key: "Display Label"` pairs | |
| `Conditions` | Optional visibility [conditions](/Skills/Conditions) | |

```yaml
  Inputs:
  - Type: option
    Key: classChoice
    Label: "Choose a Class"
    Options:
      warrior: "Warrior"
      mage: "Mage"
      ranger: "Ranger"
```


## Buttons
The `Buttons` section defines clickable action buttons. The number of buttons determines the dialog type automatically:

| Button Count | Dialog Type |
|--------------|-------------|
| 1 | Notice |
| 2 | Confirmation |
| 3+ | Multi-action (uses `Columns`) |

| Field | Description | Default |
|-------|-------------|---------|
| `Label` | Button text (MiniMessage + placeholders) | |
| `Tooltip` | Hover tooltip text | |
| `Width` | Button width in pixels | 150 |
| `Skill` | MythicMobs skill to execute on click | |
| `Conditions` | Optional visibility [conditions](/Skills/Conditions) | |

When a button is clicked, the specified skill is executed with the following variables available:
- `dialog.button` - The index of the clicked button (integer)
- `dialog.<key>` - The value of each input field, by its `Key`

```yaml
  Buttons:
  - Label: "<green>Accept"
    Tooltip: "Accept this quest"
    Width: 150
    Skill: QuestAccepted
  - Label: "<red>Decline"
    Width: 150
    Skill: QuestDeclined
```


## Exit Button
An optional close/exit button that can be added to any dialog. Works the same as a regular button.

```yaml
  ExitButton:
    Label: "Close"
    Width: 100
    Skill: OptionalCleanupSkill
```


## Conditions
Body elements, inputs, and buttons all support optional `Conditions` for per-player visibility filtering. If the conditions are not met for a player, that element is hidden from the dialog.

```yaml
  Body:
  - Type: text
    Message: "<red>VIP content!"
    Conditions:
    - hasTag:vip
  Buttons:
  - Label: "<green>VIP Shop"
    Skill: OpenVIPShop
    Conditions:
    - hasTag:vip
```


## Mechanics

### showDialog
Shows a dialog to the target player.

| Attribute | Aliases | Description | Default |
|-----------|---------|-------------|---------|
| `dialog` | `d`, `name` | The name of the dialog to show | `default` |

```yaml
Skills:
- showDialog{dialog=QuestOffer} @trigger
```

#### Aliases
- openDialog
- dialog


### closeDialog
Forcibly closes any open dialog for the target player.

```yaml
Skills:
- closeDialog @trigger
```

#### Aliases
- hideDialog


## Conditions

### hasDialogOpen
Checks if the target player currently has a dialog open.

```yaml
Conditions:
- hasDialogOpen
```

#### Aliases
- dialogOpen


## Commands

| Command | Aliases | Description | Permission |
|---------|---------|-------------|------------|
| `/mm dialogs list` | `/mm dialogs l` | Lists all loaded dialogs | `mythicmobs.command.dialogs.list` |
| `/mm dialogs show <dialog> [player]` | `/mm dialogs s`, `/mm dialogs open` | Shows a dialog to a player | `mythicmobs.command.dialogs.show` |

The parent command `/mm dialogs` can also be written as `/mm dialog` or `/mm dl`.


## Examples

### Simple Notice
```yaml
WelcomeNotice:
  Title: "<gold>Welcome!"
  Body:
  - Type: text
    Message: "<gray>Welcome to the server, <target.name>!"
  - Type: text
    Message: "<yellow>Enjoy your stay."
  Buttons:
  - Label: "<green>Got it!"
    Width: 150
```

### Quest Confirmation
```yaml
QuestOffer:
  Title: "<gold>New Quest Available"
  CanClose: true
  AfterAction: CLOSE
  Body:
  - Type: text
    Message: "<gray>A mysterious stranger needs your help."
  - Type: text
    Message: "<yellow>Reward: <green>50 Gold"
  Buttons:
  - Label: "<green>Accept"
    Tooltip: "Accept this quest"
    Width: 150
    Skill: QuestAccepted
  - Label: "<red>Decline"
    Tooltip: "Decline this quest"
    Width: 150
    Skill: QuestDeclined
```

### Character Setup with Inputs
```yaml
CharacterSetup:
  Title: "<blue>Character Setup"
  CanClose: false
  AfterAction: WAIT_FOR_RESPONSE
  Columns: 2
  Body:
  - Type: text
    Message: "<gray>Configure your character settings."
    Width: 300
  Inputs:
  - Type: text
    Key: nickname
    Label: "Display Name"
    MaxLength: 16
  - Type: bool
    Key: pvpEnabled
    Label: "Enable PvP?"
  - Type: range
    Key: difficulty
    Label: "Difficulty"
    Start: 1
    End: 10
    Initial: 5
    Step: 1
  - Type: option
    Key: classChoice
    Label: "Choose a Class"
    Options:
      warrior: "Warrior"
      mage: "Mage"
      ranger: "Ranger"
  Buttons:
  - Label: "<green>Confirm"
    Tooltip: "Save your settings"
    Width: 150
    Skill: CharacterConfirmed
  - Label: "<red>Cancel"
    Width: 150
  ExitButton:
    Label: "Close"
    Width: 100
```

In the skill triggered by the Confirm button, you can access the player's choices with:
- `<dialog.nickname>` - The entered display name
- `<dialog.pvpEnabled>` - `true` or `false`
- `<dialog.difficulty>` - The selected number
- `<dialog.classChoice>` - The selected option key (e.g. `warrior`)
- `<dialog.button>` - The button index that was clicked


<!-- LINKS -->
[Paper Dialog API]: https://docs.papermc.io/paper/dev/dialogs
[Premium Feature]: /Premium-Features