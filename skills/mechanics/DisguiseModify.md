## Description
Modifies an *already* applied disguise on the target entity.  
Like the [Disguise](/skills/mechanics/disguise) mechanic, [LibsDisguises](https://www.spigotmc.org/resources/libs-disguises-free.81/) must be installed. [Here](/Mobs/Disguises) you can find our documentation on the matter.  
The syntax for the disguise in this mechanic is completely equivalent to the one used in the `/modifydisguise` command.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| disguise  | d, type   | The options to modify in the disguise                         | player Ashijin |


## Examples
This will set the displayed item in the disguises's main has as "air"
```yaml
  Skills:
  - disguisemodify{d="setItemInMainHand air"} @self 
```

##
This will set the item displayed in the disguise's main hand as the real one
```yaml
  Skills:
  - disguisemodify{d="setItemInMainHand %held-item%"} @self
```


## Aliases
- [x] modifydisguise


<!--TAGS-->
<!--tag:Disguise-->