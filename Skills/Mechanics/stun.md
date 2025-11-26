## Description
Holds the target in place temporarily.

> This mechanic can cause Spigot to kick the player (`PlayerName moved wrongly!`)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| stopai    | ai        | Removes entity AI while stunned                                      | false   |
| gravity   | g         | Remove gravity from target when stunned (1.9+)                       | false   |
| facing    | face, f   | When false, entity cannot rotate or look around when stunned         | false   |
| noknockback | nokb, kb | When true, entity cannot be knocked back when stunned               | false   |
> This mechanic inherits every attribute of the [Aura] mechanic 
>> - The `interval` attribute is **set** at `1`
>> - The `auraGroup` attribute is **defaulted** at `#stun`

> Remember to use the aura's `duration` attribute to set a duration for the stun


## Examples
Stuns the target for 3 seconds, target cannot rotate.
```yaml
ExampleSkill:
  Skills:
  - stun{d=60;f=false} @target
```


<!-- LINKS -->
[aura]: /skills/mechanics/aura


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
<!--tag:AI-->

