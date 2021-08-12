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