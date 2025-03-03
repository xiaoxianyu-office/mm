## Description
Checks if the target mob extends the specified [Template](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Mobs/Templates)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| templates | template, t | The template to match. A list of templates can be specified, in which case the condition will match if any of the specified templates is present                              |         |


## Examples
```yaml
  Conditions:
  - templatetype{template=NetherMob,EndMob}
```


## Aliases
- [x] template
- [x] instanceOf