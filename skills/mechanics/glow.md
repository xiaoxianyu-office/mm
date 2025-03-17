## Description
Makes the target entity glow (like with the Glowing potion effect).  
This mechanic is also an [aura].

> **[Glow API](https://www.spigotmc.org/resources/api-glowapi-1-9-1-10.19422/)** is required for minecraft version 1.16.

> Please note that this mechanic is not actually giving the *glowing* effect in any form: it will just *look* like it. If you want to check against the presence of this mechanic, you must check against the presence of the applied aura (an [hasaura](/skills/conditions/hasaura) condition con do the trick, for instance)

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| auraname  | buffname, debuffname | The name of the aura                                      | #glowing|
| color     | c         | The [color] with which the entity will glow                          | white<!--type:GlowColor--> |
| audience  |           | The [audience] of the glow effect                                    | nearby<!--type:Audience--> |
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

<!-- LINKS -->
[audience]: /Skills/Audience
[color]: #color-attribute
[aura]: /skills/mechanics/aura


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
<!--tag:Effect-->