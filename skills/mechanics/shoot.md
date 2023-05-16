Mechanic: Shoot
===============

Shoots an arrow or item-projectile at the targeted entity or location
that deals damage. The shoot-mechanic has been significantly changed in
version 2.4. See below for both how it worked prior and after those
additions.

Added most of the options from the Projectile mechanic to Shoot & Volley in MM 4.11

Attributes
----------

| Attribute            | Aliases    | Description                                                                               | Default |
|----------------------|------------|-------------------------------------------------------------------------------------------|---------|
| type                 | t          | Type of projectile to shoot. Can be "arrow", "snowball", "egg", "enderpearl", or "potion" added "trident", "splash_potion", and "lingering_potion" in MM 4.11 | arrow   |
| damage               | d          | How much damage the projectile will cause                                                 | 5       |
| velocity             | v          | The velocity of the projectile                                                            | 1       |
| maxDistance          | md         | The maximum distance the projectile will travel                                           | 64      |
| vspread              | vs         | The vertical hit radius of the projectile                                                 | 0       |
| hspread              | hs         | The horizontal hit radius of the projectile                                               | 0       |
| poweraffectsvelocity | pav        | Whether the mobs power level should affect the velocity of the projectile                 | true    |
| interval             | int, i     | How often per second the projectile creates a tick-event                                  | 4       |
| ontickskill          | ontick, ot | The meta-skill to execute on each tick/interval of the projectile                         | None |
| onhitskill           | onhit, oh  | The meta-skill to execute when the projectile hits its target                             | None |
| onendskill           | onend, oe  | The meta-skill to execute when the projectile misses and ends                             | None |
| bounce               |            | Whether the projectile will bounce when it hits something                            | false |
| pickup               |            | Can pickup the item.                                                        | false |
| expiration           | duration, expire, e | How many ticks should the projectile exist for after it has landed before it gets removed                                                                  | 100     |
| accuracy             | ac, a      | Accuracy of the projectile                                          | 1 |
| knockback            | kb         | knockback strength of the projectile                                               | 0 |
| piercelevel          | pl         | The amount of times the arrow can pierce through an entity                   | 0 | 
| ignoreArmor          |            | Whether or not to ignore armor, but will still use enchantment modifiers when calculating total damage                                                                                 |     | 
| preventImmunity      |            | Whether or not to ignore immunities                                        |     | 
| preventKnockback     |            | Whether or not to prevent knockback                                         |     |
| ignoreenchants       |            | Whether or not to ignore enchantments when calculating total damage. This option is only available for 1.19+)                                                                     |     |
| damageType           |            | Sets the type of damage to be inflicted ([Extra info](/skills/mechanics/damage#elements))                                      |     | 
| damageCause          |            | Sets the damage cause for this damage mechanic ([Extra info](/skills/mechanics/damage#damagecause))                                                                        |     | 


Examples
--------

    ArrowBarrage:
      Skills:
      - shoot{type=ARROW;velocity=5;damage=10}
      - delay 10
      - shoot{type=ARROW;velocity=5;damage=10}
      - delay 10
      - shoot{type=ARROW;velocity=5;damage=10}
      - delay 10
      - shoot{type=ARROW;velocity=5;damage=10}
      - delay 10
      - shoot{type=ARROW;velocity=5;damage=10}