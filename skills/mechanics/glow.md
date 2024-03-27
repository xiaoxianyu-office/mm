## Description
Makes the target entity glow (using the Glowing potion effect.).  
This mechanic is also an [aura].

Can have a color specified.  

Can have an [audience].  

> **[Glow API](https://www.spigotmc.org/resources/api-glowapi-1-9-1-10.19422/)** is required for minecraft version 1.16.

## Valid Colors

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



## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| color     | c         | The [color] with which the entity will glow                          | white   |
| duration  | d         | How long the effect will last                                        | 100     |
| audience  |           | The [audience] of the glow effect                                    | nearby  |

> This mechanic inherits every attribute of the [Aura] mechanic 
>> - The `auraname` attribute is **defaulted** at `#glowing`
>> - The `charges` attribute is **set** at `1` and cannot be modified.  
>> - The `maxStacks` attribute is **set** at `1` and cannot be modified.  
>> - The `mergeAll` attribute is **set** at `true` and cannot be modified.  

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

<!-- LINKS -->
[audience]: Skills/Audience
[color]: #valid-colors
[aura]: skills/mechanics/aura
