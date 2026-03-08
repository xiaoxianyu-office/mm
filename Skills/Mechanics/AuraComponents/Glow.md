## Description
Makes the target entity glow (like with the Glowing potion effect).  

> Please note that this mechanic is not actually giving the *glowing* effect in any form: it will just *look* like it. If you want to check against the presence of this mechanic, you must check against the presence of the applied aura (an [hasaura](/skills/conditions/hasaura) condition con do the trick, for instance)

[audience]: /Skills/Audience
[color]: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Color.html
[aura]: /skills/mechanics/aura

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| color     | c         | The [color] with which the entity will glow                          | white<!--type:GlowColor--> |
| audience  |           | The [audience] of the glow effect                                    | nearby<!--type:Audience--> |


<!--TAGS-->
<!--tag:Aura:Component-->
