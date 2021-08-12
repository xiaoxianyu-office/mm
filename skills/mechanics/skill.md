Mechanic: Skill
===============

Executes another meta-skill, which must be located in
*/MythicMobs/Skills*. The executed skill will inherit any targets if no
targeter is specified.

Syntax
------

    Skills:
    - skill{skill=AnotherSkill} @Target ~onAttack
    - skill{s=AnotherSkill} @Trigger ~onSpawn
    - skill:OtherSkill @Trigger ~onDeath


The attribute "sync=true" will be inherited by any sub-skills and cannot
be set to *false* later in a skill-tree.

| Attribute | Shorthand | Description                                                         | Default |
|-----------|-----------|---------------------------------------------------------------------|---------|
| forcesync | sync      | Whether to force the skill to be run synchroniously with Minecraft. | false   |

Cooldown
--------

Skill configurations are capable of utilizing cooldown
Add cooldown to your skills like this:

    internal_skillname:
      Cooldown: <seconds>
      Conditions:
      - condition
      - ...
      Skills:
      - mechanic{}
      - ...

Note that this only applies for skill configurations that are saved as
skill-files in */MythicMobs/Skills*. Cooldown can't be added to
mechanics called directly in mob configuration files.

Examples
--------

    Skills:
    - skill{s=AnotherSkill;sync=true} @Target ~onAttack
    - skill{s=ice_bolt;sync=true} @Target ~onTimer:100
    - skill{sync=true;s=flamethrower} @TargetLocation ~onTimer:200
    - skill:Onemechainc @Target ~onDamaged
    - skill
        {
        skill=leafs;
        sync=true
        }