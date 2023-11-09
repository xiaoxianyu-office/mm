## Description
Makes the target entity glow (using the Glowing potion effect.)  

Can have a color specified.  

Can have an [audience]

> **[Glow
Api](https://www.spigotmc.org/resources/api-glowapi-1-9-1-10.19422/)** is required for minecraft versions below 1.18


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| color     | c         | The [color] with which the entity will glow                          | white   |
| duration  | d         | How long the effect will last                                        | 100     |
| audience  |           | The [audience] of the glow effect                                    | nearby  |


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
[audience]: Skills/Effects#audience
[color]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/ChatColor.html