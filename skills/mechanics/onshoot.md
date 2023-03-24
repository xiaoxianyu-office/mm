Mechanic: onShoot
=================

Applies an aura to the target that triggers a skill when they shoot with a bow. Can use any [aura](/skills/mechanics/aura) attribute

Attributes
----------

| Attribute        | Aliases       | Description                                                | Default Value |
|------------------|---------------|------------------------------------------------------------|---------------|
| onShoot            | osh            | Skill to execute when the entity shoots            |               |
| cancelEvent      | cE            | Whether or not to cancel the event that triggered the aura | false         |
| forceaspower        | fap       | Whether to pass the force of the bow as the skill's power | true             |

  

Examples
--------

      Skills:
      - onShoot{auraName=fireball_bow;onShoot=[ shootfireball ];duration=200;charges=5} @self
      - ...

In this example, the caster's next 5 bow shots will shoot fireballs
instead of arrows.