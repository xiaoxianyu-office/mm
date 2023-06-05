Mechanic: CancelEvent
=====================

Cancel the Event that triggered the skill. This mechanic has several
important requirements in order to execute properly:

-   The mechanic (or the first skill that leads to it) must be run with
    sync=true in the mob's skill list. Example: -
    skill{s=CancelEventSkill;sync=true} ~onDamaged
-   No delays allowed.
-   It only works with specific triggers that make sense.

Possible Triggers
-----------------

-   ~onAttack
-   ~onDamaged
-   ~onExplode
-   ~onInteract
-   ~onCombat
-   ~onTeleport
-   ~onShoot (Requires Crucible for a bow / crossbow)
-   ~onUse (Requires Crucible)
-   ~onConsume (Requires Crucible)

Example
-------

Skill.yml:

    CancelDamageEvent:
      Skills:
      - CancelEvent
      - message{m="&cYou cannot hurt this mob!"} @trigger

Mob.yml:

    NoDamageMob:
      Type: villager
      Skills:
      - skill{s=CancelDamageEvent;sync=true} ~onDamaged

Or to prevent a skeleton from shooting:

    customskeleton:
      Type: skeleton
      Skills:
      - cancelevent{sync=true} ~onShoot