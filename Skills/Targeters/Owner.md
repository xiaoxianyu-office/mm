## Description
Targets the Owner of the casting mob.  
The Owner can be set via the [SetOwner](/Skills/mechanics/setowner) mechanic.


## Attributes
>*This targeter has no attributes*


## Examples
This metaskill will send a message to the Owner of the casting mob
```yaml
ExampleSkill:
  Skills:
  - message{m="Hello there!"} @Owner
```