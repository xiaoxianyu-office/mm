Mechanic: onDamaged
===================

Applies an aura to the target that triggers a skill when they take
damage. Can use any aura attribute

Attributes
----------

| Attribute        | Aliases       | Description                                                | Default Value |
|------------------|---------------|------------------------------------------------------------|---------------|
| onHit            | oH            | Skill to execute if the target is damaged                  | NONE        |
| cancelEvent      | cE            | Whether or not to cancel the event that triggered the aura | false         |
| damageAdd        | add, a        | An optional static increase to the original hit's damage | 0             |
| damageSub        | sub, s        | An optional static decrease (or increase if negative) to the original hit's damage | 0             |
| damageMultiplier | multiplier, m | An optional multiplier on the original hit's damage      | 1            |
| damageMods       |               | Allows the aura to apply damage modifiers. Also accepts a list, as shown in the example. Placeholders can be used as the modifier's amount (**Premium only**). |              |

Examples
--------

      Skills:
      - onDamaged{
          auraName=damageResist;d=200;
          onTick=[
            - particles{p=flame;amount=10;hS=0.4}
          ];
          damageMods="FIRE 0.5, MAGIC 0.3, CUSTOM <caster.var.customresistance>"} @self ~onInteract
      - ...