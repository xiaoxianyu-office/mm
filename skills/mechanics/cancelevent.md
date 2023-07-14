Mechanic: CancelEvent
=====================

Cancel the Event that triggered the skill. This mechanic has several
important requirements in order to execute properly:

-   The mechanic or initial skill must be run with sync=true. Example: -
    skill{s=CancelEventSkill;sync=true} ~onDamaged
-   No delays allowed.
-   Not all triggers support it. 
-   Other mechanics within that skill can still be triggered.

Possible Triggers
-----------------

-   ~onAttack
-   ~onDamaged
-   ~onDeath
-   ~onExplode
-   ~onInteract
-   ~onCombat
-   ~onTeleport
-   ~onShoot (Requires Crucible for a bow / crossbow if the caster is a player)
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