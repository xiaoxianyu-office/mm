## Description
Hides the caster from the targeted players for a set duration.  

> The hidden entity can then be shown via the used of the [showentity] mechanic.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| auraname  | buffname, debuffname | The name of the aura                                      | #hiding |
| ignoreAuraOptions| iao, permanent, perma | This will make the mechanic ignore any [aura]-related option and the `duration` attribute      | false   | 

> This mechanic inherits every attribute of the [Aura] mechanic  
>> - The `auraname` attribute is **defaulted** at `#hiding`
>> - The `charges` attribute is **set** at `1`  
>> - The `maxStacks` attribute is **set** at `1`  
>> - The `mergeAll` attribute is **set** at `true`  


## Examples
```yml
DUMMY:
  Type: ZOMBIE
  Skills:
  - hide{d=100} @Server ~onInteract
```
##
```yml
CUSTOM_ITEM:
  Id: STICK
  Skills:
  - hide{d=100} @Server ~onUse #User is now invisible from all online players, no armor is shown
```


## Aliases
- [x] hideFromPlayers
- [x] hideFromPlayer


<!-- LINKS -->
[aura]: /skills/mechanics/aura
[showentity]: /skills/mechanics/showentity



<!--TAGS-->
<!--tag:Effect-->
<!--tag:Meta-Mechanic:Aura-->

