Custom Menus are a special feature added by MythicMobs Premium (or by using MythicRPG with MythicMobs free) that allows you to make, well, custom menus!

> **This feature requires either [MythicMobs Premium](/Premium-Features) or [MythicRPG](https://mythiccraft.io/index.php?resources/mythicrpg-spells-classes-professions-more.129/) to be used!**

[[_TOC_]]

# Custom Menus
### Creating Menus
You can create menus by placing them in any `.yml` file inside a `menus` folder in any mythic pack.

For example, you can create a new `.yml` file at `plugins/MythicMobs/menus/custom_menus.yml`. 

Any top-level node will be loaded as a menu using the standard Mythic menu format. For example, to create a menu named `MyCustomMenu` you'd place this in the file:
```yaml
MyCustomMenu:
  Display: "My Custom Menu"
  Size: 27
  Shared: false # Whether the Menu should not be cached and shared across players
  Schema:
    - '1 1 1 1 1 1 1 1 1'
    - '0 0 0 0 B 0 0 0 0'
    - '1 1 1 1 1 1 1 1 1'
  Icons:
    FILLER:
      Mapping: 1
      Material: RED_STAINED_GLASS_PANE
      Display: ''
      Model: 1
    TEST_BUTTON:
      Mapping: B
      Material: GOLD_INGOT
      Model: 4
      Display: 'Test'
      Skills:
      - sound{s=entity.chicken.egg}
      - setcustommenubutton{slot=11;icon=DYNAMIC_BUTTON}
      - message{m="you hit me"} @self
    DYNAMIC_BUTTON:
      Material: IRON_SWORD
      Model: 100
```

This example includes many of the features of the custom menu system.

The `Schema` defines how the menu looks - it's basically a `9 x height` grid representing the menu's icons. Each letter/number is mapped to one of the icons defined under the `Icons` section.

For example, any slot in the Schema with 1 is mapped to FILLER:
```yaml
    FILLER:
      Mapping: 1
```

Icons contain:
- `Mapping`: a letter or number used to map the icon to the schema
- `Material`: the Material of the icon
- `Model`: the CustomModelData of the icon
- `Display`: the Display Name of the icon
- `Lore`: a list of lines of lore
- `Skills`: Skills executed when the button is pressed

### Modifying a Menu
You can modify an open menu using the `setcustommenubutton{slot=11;icon=ICON}` mechanic

### Opening Menus
To open a custom menu you've created, you can use one of the following:
- **`Command`** - `/mm menus open [menu] <player>`
- **`Mechanic`** - the `openCustomMenu{menu=name}` mechanic

# Button Skills
As shown above, each button in the menu can have a set of skills associated with it. Once the button is clicked, the skills are executed.  

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.click-type>`       |

```yaml
  Skills:
  - sound{s=entity.chicken.egg}
  - message{m="<skill.var.click-type>"} @self
```


<!-- LINKS -->
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders