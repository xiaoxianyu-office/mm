## Description
Applies an aura component to the target that triggers a skill when they shoot with a bow. Can use any [aura] attribute

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.bow-tension>`      |


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onShootSkill | onshoot, osh, onbowshoot, onbowshootskill | Skill to execute when the entity shoots |<!--type:Metaskill-->|
| cancelEvent | cE      | Whether or not to cancel the event that triggered the aura           | false   |


## Examples
```yaml
  Skills:
    - aura{auraName=fireball_bow;duration=200;charges=5;components=[
      - onShoot{onShoot=[ shootfireball ];cancelEvent=true} @self
      ]} @self
```
In this example, the caster's next 5 bow shots will shoot fireballs
instead of arrows.


## Aliases
- [x] onbowshoot


<!-- LINKS -->
[aura]: /skills/mechanics/aura
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders

<!--TAGS-->
<!--tag:Event-->
