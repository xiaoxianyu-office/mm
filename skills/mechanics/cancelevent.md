## Description

Cancel the Event that triggered the skill. This mechanic has several
important requirements in order to execute properly:

-   **The mechanic or initial skill must be run with sync=true. Example: -
    skill{s=CancelEventSkill;sync=true} ~onDamaged**
-   No delays allowed.
-   Not all triggers support it. 
-   Other mechanics within that skill can still be triggered.

### Compatible Triggers

-   ~onAttack
-   ~onBucket
-   ~onDamaged
-   ~onDeath
-   ~onExplode
-   ~onInteract
-   ~onCombat
-   ~onTeleport
-   ~onShoot (Requires Crucible for a bow / crossbow if the caster is a player)
-   ~onUse (Requires Crucible)
-   ~onConsume (Requires Crucible)

## Examples

Skill.yml:
```yaml
CancelDamageEvent:
  Skills:
  - CancelEvent
  - message{m="&cYou cannot hurt this mob!"} @trigger
```
Mob.yml:
```yaml
NoDamageMob:
  Type: villager
  Skills:
  - skill{s=CancelDamageEvent;sync=true} ~onDamaged
```
You can use it in-line too! This example will prevent the mob from shooting its bow, and from taking any damage.
```yaml
customskeleton:
  Type: skeleton
  Skills:
  - cancelevent{sync=true} @self ~onShoot
  - cancelevent{sync=true} @self ~onDamaged
```