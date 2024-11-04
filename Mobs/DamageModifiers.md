## Damage Modifiers

Damage Modifiers are an attribute you can add to your MythicMobs to increase or decrease the damage they receive from various sources.  

Let's say an entity takes damage by a `ENTITY_ATTACK` type of damage and of amount `10`. Depending on the value of its associated DamageModifier, different things will happen:
- `A value > 0`: The amount of the damage would be multiplied by the value itself. If the value was `2`, the damage would be doubled. If it was `0.5`, it will be halved.
- `A value of 0`: The damage event will not cause any damage, but would still play the damage animation
- `A value < 0`: the associated damage event will be cancelled and the caster would be healed by the amount of the original damage multiplied by the absolute value of the damage modifier. If the value was `-2`, the caster would be healed by `20` hit points. If it was `-0.1`, it would be healed by `1` hit point. 

Some of these won't work on certain mobs under normal circumstances (e.g. SUICIDE, as no mob naturally suicides).  
Damage Modifiers are completely optional, you only need to add the ones you want to use.  

See the [spigot javadocs](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html) for a complete list of available damage types.

## Options

| Modifier            | Explanation                                                        |
| ------------------- | ------------------------------------------------------------------ |
| BLOCK_EXPLOSION     | Damage caused by being in the area when a block explodes.          |
| CAMPFIRE            | Damage caused when an entity steps on `CAMPFIRE` or `SOUL_CAMPFIRE`. |
| CONTACT             | Damage caused when an entity contacts a block such as a Cactus,  Dripstone (Stalagmite) or Berry Bush. |
| CRAMMING            | Damage caused when an entity is colliding with too many entities due  to the maxEntityCramming game rule. |
| CUSTOM              | Custom damage.                                                     |
| DRAGON_BREATH       | Damage caused by a dragon breathing fire.                          |
| DROWNING            | Damage caused by running out of air while in water                 |
| DRYOUT              | Damage caused when an entity that should be in water is not.       |
| ENTITY_ATTACK       | Damage caused when an entity attacks another entity.               |
| ENTITY_EXPLOSION    | Damage caused by being in the area when an entity, such as a  Creeper, explodes. |
| ENTITY_SWEEP_ATTACK | Damage caused when an entity attacks another entity in a sweep attack. |
| FALL                | Damage caused when an entity falls a distance greater than 3 blocks |
| FALLING_BLOCK       | Damage caused by being hit by a falling block which deals damage   |
| FIRE                | Damage caused by direct exposure to fire                           |
| FIRE_TICK           | Damage caused due to burns caused by fire                          |
| FLY_INTO_WALL       | Damage caused when an entity runs into a wall.                     |
| FREEZE              | Damage caused from freezing.                                       |
| HOT_FLOOR           | Damage caused when an entity steps on `MAGMA_BLOCK`.               |
| KILL                | Damage caused by /kill command                                     |
| LAVA                | Damage caused by direct exposure to lava                           |
| LIGHTNING           | Damage caused by being struck by lightning                         |
| MAGIC               | Damage caused by being hit by a damage potion or spell             |
| MELTING             | Damage caused due to a snowman melting                             |
| POISON              | Damage caused due to an ongoing poison effect                      |
| PROJECTILE          | Damage caused when attacked by a projectile.                       |
| SONIC_BOOM          | Damage caused by the Sonic Boom attack from `Warden`               |
| STARVATION          | Damage caused by starving due to having an empty hunger bar        |
| SUFFOCATION         | Damage caused by being put in a block                              |
| SUICIDE             | Damage caused by committing suicide.                               |
| THORNS              | Damage caused in retaliation to another attack by the Thorns  enchantment. |
| VOID                | Damage caused by falling into the void                             |
| WITHER              | Damage caused by Wither potion effect                              |
| WORLD_BORDER        | Damage caused by the World Border                                  |

<!--
These Options are automatically generated via a script. Do not edit them directly.
-->



## Examples

NOTE: A modifier of 1 will cause the mob to take normal damage from that source. A number higher than 1 will multiply the damage it takes by that amount. A number lower than 1 will reduce the damage it takes by that amount. And 0 will make the mob immune to that damage source.
A negative value will cause the mob to heal from that type of damage. Note that this doesn't work if the mob is naturally immune to that damage, E.g. Iron Golems with FALL, Blazes with FIRE, FIRE_TICK, or LAVA. Etc.

In this first example our Armored Zombie mob is just a basic MythicMob with nothing added to it.

```yaml
ArmoredZombie:
  Mobtype: zombie
  Display: '&aArmored Zombie'
  Health: 40
  Damage: 6
```

But, if we add the DamageModifiers attribute to him we can start messing around with his weaknesses and resistances. In this example we are going to make it so melee and projectile attacks only do 75% of their normal damage to our Armored Zombie.

```yaml
ArmoredZombie:
  Mobtype: zombie
  Display: '&aArmored Zombie'
  Health: 40
  Damage: 6
  DamageModifiers:
  - ENTITY_ATTACK 0.75
  - PROJECTILE 0.75
```

Alright, we have our damage resistant zombie now. Any melee and projectile damage it receives will be reduced by 25% (This includes from players and other mobs.) but now he seems a little overpowered, so, lets give him a weakness to go along with it.

```yaml
ArmoredZombie:
  Mobtype: zombie
  Display: '&aArmored Zombie'
  Health: 40
  Damage: 6
  DamageModifiers:
  - ENTITY_ATTACK 0.75
  - PROJECTILE 0.75
  - MAGIC 1.25
```

Our little Armored Zombie is still well protected against projectile and melee attacks, but we have given him a weakness to magic (splash health potions) to compensate.


Our second example is a fire elemental, not only does this mob not take damage from burning, it also heals health when standing in fire, and regains even more health when in lava. Note: This DOES NOT work on Nether mobs as they don't take damage from fire at all, preventing them from having their fire and lava damage modified.

```yaml
FireElemental:
  Mobtype: zombie
  Display: '&cFire Elemental'
  Health: 20
  DamageModifiers:
  - FIRE -1
  - LAVA -4
  - FIRE_TICK 0
```