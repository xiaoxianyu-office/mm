## Description
Undoes a previous paste done via the [fawePaste] mechanic, based on its id or on the schematic used


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| pasteID   | pid, id   | The id of the paste that needs to be undone                          |         |
> This mechanic inherits every *inheritable* attribute of the [Aura](/Skills/Mechanics/Aura) mechanic


## Examples
```yaml
ExampleMob:
  Skills:

  # With ID
  - fawePaste{s=cgym.schem;id=abc} @self ~onSpawn
  - undoPaste{id=abc} @self ~onDamaged

  # Without ID
  - fawePaste{s=lab.schem} @self ~onSpawn
  - undoPaste{id=lab.schem} @self ~onDamaged
```


## Aliases
- [x] undoschem
- [x] undoschematic


<!-- LINKS -->
[fawePaste]: /Skills/mechanics/fawepaste/


<!--TAGS-->
<!--tag:World-->
