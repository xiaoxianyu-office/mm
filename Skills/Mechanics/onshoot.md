## Description
Applies an aura to the target that triggers a skill when they shoot with a bow. Can use any [aura] attribute

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.bow-tension>`      |


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onShootSkill | onshoot, osh, onbowshoot, onbowshootskill | Skill to execute when the entity shoots |<!--type:Metaskill-->|
| cancelEvent | cE      | Whether or not to cancel the event that triggered the aura           | false   |
| forceaspower | fap    | Whether to pass the force of the bow as the skill's power            | true    |

> This mechanic inherits every attribute of the [aura] mechanic


## Examples
```yaml
  Skills:
  - onShoot{auraName=fireball_bow;onShoot=[ shootfireball ];duration=200;charges=5;cancelEvent=true} @self
```
In this example, the caster's next 5 bow shots will shoot fireballs
instead of arrows.


## Aliases
- [x] onbowshoot


<!-- LINKS -->
[aura]: /skills/mechanics/aura
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
