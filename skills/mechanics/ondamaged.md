Mechanic: onDamaged
===================

Applies an aura to the target that triggers a skill when they take
damage. Can use any aura attribute

Attributes
----------

| Attribute        | Aliases       | Description                                                | Default Value |
|------------------|---------------|------------------------------------------------------------|---------------|
| onHit            | oH            | Skill to execute if the target is damaged                  |               |
| cancelEvent      | cE            | Whether or not to cancel the event that triggered the aura | false         |
| damageSub       | sub, s        | An optional static decrease (or increase if negative)
    to the original hit's damage | 0             |
| damageMultiplier | multiplier, m | An optional multiplier on the original hit's
    damage | 1             |

  

Examples
--------

      Skills:
      - onDamaged{
          auraName=damageResist;d=200;
          onTick=[
            - particles{p=flame;amount=10;hS=0.4}
          ];
          damageMods="FIRE 0.5"} @self ~onInteract
      - ...