[[_TOC_]]

# AI Goal Selectors
Goal Selectors are used with the AIGoalSelectors field and determine what mobs want to “do”. Certain custom goals might not work if they're not included in the base AI of the mob you're creating. For example, a zombie won't be able to use the AI goal “EatGrass” because a zombie would never use that goal in the first place. Feel free to experiment to figure out what does and doesn't work!

Note: Certain goals will not work correctly if the world is in peaceful mode.

Example:

```yaml
SuperMob:
  Type: zombie
  Health: 200
  Display: 'Superb Zombie'
  AIGoalSelectors:
  - clear
  - meleeattack
  - randomstroll
```

This zombie would attack players, and walk around randomly when not targeting an enemy.

## All Mobs
| AI Goal            | Aliases      | Description                                                        |
|--------------------|--------------|--------------------------------------------------------------------|
| clear              | reset        | Removes the AI from the mob                                        |
| [breakdoors](/Mobs/ai/goals/BreakDoor) |              | Causes the mob to break down doors it runs into                    |
| [eatgrass](/Mobs/ai/goals/EatGrass) | | Makes the mob occasionally… eat grass                          |
| [float](/Mobs/ai/goals/Float) | swim         | Makes the mob swim in water/not                         |
| [lookatplayers](/Mobs/ai/goals/lookatplayers) | | The mob will look at nearby players                  |
| [LookAtTarget](/Mobs/ai/goals/LookAtTarget) | | The mob will look at its target                        |
| [opendoor](/Mobs/ai/goals/OpenDoor)| opendoors | The mob will open doors it runs into and close the door behind it  |
| [randomlookaround](/Mobs/ai/goals/RandomLookAround) | lookaround   | The mob will randomly look around                                  |
| [gotospawnlocation](/Mobs/ai/goals/gotospawn) | gotospawn | Mob will pathfind to its spawn location    |
| [doNothing](/Mobs/ai/goals/doNothing)<br>**[Premium-only]** | | Causes the mob to do nothing if conditions are met.                                                                                      |

## Creatures Only
| AI Goal            | Aliases      | Description                                                        |
|--------------------|--------------|--------------------------------------------------------------------|
| [meleeattack](/Mobs/ai/goals/meleeattack) | | Causes the mob to move to and melee-attack its target    |
| [movetowardstarget](/Mobs/ai/goals/MoveTowardsTarget) | | Causes the mob to move towards its target    |
| [randomstroll](/Mobs/ai/goals/RandomStroll) |              | The mob will randomly walk around         |
| [restrictsun](/Mobs/ai/goals/RestrictSun) | | Will prevent the mob from entering sunlight              |
| [fleeplayers](/Mobs/ai/goals/fleeplayers) | runfromplayers | Causes the mob to avoid Players           |
| [fleegolems](/Mobs/ai/goals/fleegolems) | runfromgolems | Causes the mob to avoid Iron Golems          |
| [fleevillagers](/Mobs/ai/goals/fleevillagers) | runfromvillagers | Causes the mob to avoid villagers   |
| [fleewolf](/Mobs/ai/goals/fleewolf) | runfromwolves | Causes the mob to avoid wolves                   |
| [fleefaction](/Mobs/ai/goals/fleefaction) | runfromfaction | Causes the mob to avoid entities in a given faction                                                                                            |
| [fleesun](/Mobs/ai/goals/fleesun) | | The mob will hide in the shade when the sun it out               |
| [fleeConditional](/Mobs/ai/goals/fleeconditional)<br>**[Premium-only]** | fleeIf | Causes the mob to flee based on provided conditions. Safe speed is required for distances greater than 5                   |
| [spiderattack](/Mobs/ai/goals/SpiderAttack) | | Uses the attack a spider would                         |
| [zombieattack](/Mobs/ai/goals/ZombieAttack) | | Zombie melee attack                                    |
| [leapattarget](/Mobs/ai/goals/leapattarget) | | Makes the mob leap at its target                       |
| [movethroughvillage](/Mobs/ai/goals/movethroughvillage) |              |                              |
| [movetoblock](/Mobs/ai/goals/movetoblock)| | Makes the mob go towards a specific type of block         |
| [movetolava](/Mobs/ai/goals/movetolava) | | Makes the mob move towards lava                            |
| [movetowater](/Mobs/ai/goals/movetowater) | | Makes the mob move towards water                         |
| [movetowardsrestriction](/Mobs/ai/goals/MoveTowardsRestriction) |            | Make a mob move towards its "Restriction Point" for some Entities (for instance, the village of a Villager) |
| [MoveWithinDistanceOfTarget](/Mobs/ai/goals/MoveWithinDistanceOfTarget) | | Moves towards the target to be within a certain range    |
| [MoveTowardsTargetConditional](/Mobs/ai/goals/MoveTowardsTargetConditional) | | Paths to an entity that checks some conditions    |
| [FollowRoute](/Mobs/ai/goals/FollowRoute) | followpath | Makes the mob follow a specific path, one time only. | 
| [patrol](/Mobs/ai/goals/Patrol) x1,y1,z1;x2,y2,z2;x3,y3,z3;… | patrolroute | Makes the mob patrol between the specified locations |
| [gotolocation](/Mobs/ai/goals/GoToLocation) x,y,z | goto           | Makes the mob go to the specified location(Notice Followrange must more than the distance between location and mob)                        |
| [gotoowner](/Mobs/ai/goals/GoToOwner) # |                | Makes the mob move towards its [owner](/Skills/Targeters/Owner) when beyond a certain distance (defaults to 5 blocks)<br>[Followrange](/Mobs/Options#followrange) must be more than the distance between the owner and the mob)                                                    |
| [gotoparent](/Mobs/ai/goals/GoToParent) |       | Makes the mob move towards its parent mob            |
| [Panic](/Mobs/ai/goals/Panic) | panicWhenOnFire | Run around panicking when on fire and look for water |
| [randomFly](/Mobs/ai/goals/RandomFly) |               | Fly around randomly                            |
| [randomNod](/Mobs/ai/goals/RandomNod) |         | Makes the mob randomly nod its head                  |
| [horrified](/Mobs/ai/goals/Horrified) |         | Run around frantically                               |

## Animals Only
| AI Goal            | Aliases      | Description                                                        |
|--------------------|--------------|--------------------------------------------------------------------|
| [breed](/Mobs/ai/goals/breed) |   | Causes the mob to be able to breed with other mobs                 |

## Creepers Only
| AI Goal            | Aliases      | Description                                                        |
|--------------------|--------------|--------------------------------------------------------------------|
| [creeperswell](/Mobs/ai/goals/CreeperSwell) | creeperexplode | Make a creeper want to explode on its target                     |

## Ranged Entities Only
| AI Goal            | Aliases      | Description                                                        |
|--------------------|--------------|--------------------------------------------------------------------|
| [rangedattack](/Mobs/ai/goals/arrowattack) | arrowattack         | A basic ranged/projectile attack    |
| [bowattack](/Mobs/ai/goals/bowattack)      | bowshoot, bowmaster | An advanced bow attack.             |

## Piglins and Pillagers Only
| AI Goal            | Aliases      | Description                                                        |
|--------------------|--------------|--------------------------------------------------------------------|
| [crossbowAttack](/Mobs/ai/goals/crossbowattack) | | attack with a crossbow                             |


# AI Target Selectors
Target Selectors are used with the AITargetSelectors field and determine what mobs try to target.

> If the mob has AITargets but not AIGoal that allows them to act based on their target, they will *still* be considered to have valid targets chosen according to the AITargets used (so, for instance, a @target targeter can be used and so on)

Example
```yaml
SuperMob:
  Type: zombie
  Health: 200
  Display: 'Superb Zombie'
  AIGoalSelectors:
  - clear
  - meleeattack
  - randomstroll
  AITargetSelectors:
  - clear
  - players
  - golems
```

## All Creatures
| AI Target          | Aliases      | Description                                                        |
|--------------------|--------------|--------------------------------------------------------------------|
| clear              |              | Special Option. Clears all of the mob's AI                         |
| [hurtbytarget](/Mobs/ai/targets/HurtByTarget) | attacker, damager | Targets whatever attacks the mob   |
| [monsters](/Mobs/ai/targets/Monsters) | monster | Targets monsters                                     |
| [Players](/Mobs/ai/targets/Players) | player | Targets players                                         |
| [Villagers](/Mobs/ai/targets/Villagers) | villager | Targets villagers                                 |
| [irongolem](/Mobs/ai/targets/Irongolems) | irongolem, iron_golems, iron_golem | Targets Golems         |
| [nearestConditionalTarget](/Mobs/ai/targets/nearestconditionaltarget)<br>**[Premium-only]**            | nearestConditional, nearestIf | Targets the nearest entity that meets the conditions provided            |
| [OwnerAttacker](/Mobs/ai/targets/OwnerAttacker) | ownerHurtBy, ownerHurtByTarget, ownerDamager | Targets whatever attacks the mob's owner |
| [OwnerTarget](/Mobs/ai/targets/OwnerTarget) | ownerAttack, ownerhurt | Targets whatever the mob's owner attacks.                |
| [ParentHurtBy](/Mobs/ai/targets/ParentHurtBy) | parentHurtByTarget, parentDamager, parentAttacker | Targets the entity that attacks the mob's parent       |
| [ParentTarget](/Mobs/ai/targets/ParentTarget) | parentHurt, parentAttack | Targets the entity that is being hit by the caster's parent |

## All Creatures ([Faction](/Mobs/Factions) Support)
| AI Target          | Aliases      | Description                                                        |
|--------------------|--------------|--------------------------------------------------------------------|
| [NearestOtherFaction](/Mobs/ai/targets/NearestOtherFaction) | OtherFaction | Targets ANY entities that are in a different faction |
| [NearestOtherFactionMonsters](/Mobs/ai/targets/NearestOtherFactionMonsters) | OtherFactionMonsters | Targets any monster that is in a different faction |
| [SpecificFaction](/Mobs/ai/targets/specificfaction) [faction_name] | | Targets any entities that are in the given faction                                                                                        |
| [SpecificFactionMonsters](/Mobs/ai/targets/specificfactionmonsters) [faction_name] | | Targets any monsters that are in the given faction                                                                   |