## Description
Sets the EnderDragon phase on the target EnderDragon entity


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| phase     | p         | The phase to set                                                    | CIRCLING<!--type:EnderDragonPhase--> |

### Phase Attribute
The possible values of the phase attribute (at the time of writing) are listed below.  
The most up to date list can be found in the [javadoc](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EnderDragon.Phase.html).  

| Phase                 | Description                                                                    |
|-----------------------|--------------------------------------------------------------------------------|
| BREATH_ATTACK         | The dragon will attack with dragon breath at its current location              |
| CHARGE_PLAYER         | The dragon will charge a player                                                |
| CIRCLING              | The dragon will circle outside the ring of pillars if ender crystals remain or inside the ring if not  |
| DYING                 | The dragon will fly to the vicinity of the portal and die                      |
| FLY_TO_PORTAL         | The dragon will fly towards the empty portal (approaching from the other side, if applicable) |
| HOVER                 | The dragon will hover at its current location, not performing any actions      |
| LAND_ON_PORTAL        | The dragon will land on on the portal                                          |
| LEAVE_PORTAL          | The dragon will leave the portal                                               |
| ROAR_BEFORE_ATTACK    | The dragon will roar before performing a breath attack                         |
| SEARCH_FOR_BREATH_ATTACK_TARGET | The dragon will search for a player to attack with dragon breath     |
| STRAFING              | The dragon will fly towards a targeted player and shoot a fireball when within 64 blocks |


## Examples
```yaml
  Skills:
  - enderDragonSetPhase{p=CHARGE_PLAYER} @self ~onDamaged 0.2
```
> The dragon will charge a player after being damaged. Please note that is not possible to determine which player will be targeted by the dragon


## Aliases
- [x] setEnderDragonPhase