::include{file=/Skills/Mechanics/AuraComponents/Glow.md}
> This mechanic inherits every attribute of the [Aura] mechanic 
>> - The `auraname` attribute is **defaulted** at `#glowing`
>> - The `charges` attribute is **set** at `1` and cannot be modified.  
>> - The `maxStacks` attribute is **set** at `1` and cannot be modified.  
>> - The `mergeAll` attribute is **set** at `true` and cannot be modified.  


### Color Attribute
|    VALID     |   COLORS     |
|:------------:|:------------:|
| BLACK        | DARK_GRAY    |
| DARK_BLUE    | BLUE         |
| DARK_GREEN   | GREEN        |
| DARK_AQUA    | AQUA         |
| DARK_RED     | LIGHT_PURPLE |
| DARK_PURPLE  | YELLOW       | 
| GOLD         | WHITE        |
| GRAY         | RED          |


## Examples
Makes the target glow red for 1000 ticks (50 seconds).
```yaml
  Skills:
  - effect:glow{color=RED;duration=1000}
```

## Aliases
- [x] effect:glow
- [x] e:glow
- [x] glow


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
<!--tag:Effect-->