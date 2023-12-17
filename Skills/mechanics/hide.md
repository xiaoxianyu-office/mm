## Description
Hides the caster from the targeted players for a set duration.  
A duration of `0` will permanently hide the caster.  
Only works for MC 1.18+.  
This mechanic is also an [aura].  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| duration  | d         | The given duration                                                   | 0       |

> This mechanic inherits every attribute of the [Aura] mechanic  
>> - The `auraname` attribute is defaulted at `#hiding`  
>> - The `charges` attribute is defaulted at `1`  
>> - The `maxStacks` attribute is defaulted at `1`  
>> - The `mergeAll` attribute is defaulted at `true`  


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


<!-- LINKS -->
[aura]: skills/mechanics/aura