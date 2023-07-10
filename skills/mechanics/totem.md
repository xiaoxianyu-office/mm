Mechanic: Totem
---------------

The totem mechanic places an invisible "totem", similar to the
[projectile](/skills/mechanics/projectile) mechanic, except that it
doesn't move. Much like projectiles, you can use onTick skills to create
effects in order to identify the totem's location.

Totems will pulse their onHit skill on any targets that come within
their defined radius until their charges or duration run out. They're
useful for creating ground effects with particles, such as clouds of
poison or land mines.

Attributes
----------

| Attribute        | Aliases     | Description                                                                                     | Default Value     |
|------------------|-------------|-------------------------------------------------------------------------------------------------|-------------------|
| Charges          | ch, c       | Determines how many times the totem can hit something before disappearing.                      | 0                 |
| onTick           | oT          | Meta-Skill executed every [interval] ticks at the projectile's origin location.               | None              |
| onHit            | oH          | Meta-Skill executed when the totem hits something. Targets hit are inherited by the meta-skill. | None              |
| onEnd            | oE          | Meta-Skill executed when the totem ends.                                                        | None              |
| onStart          | oS          | Meta-Skill executed when the totem starts.                                                      | None              |
| Interval         | i, int      | How often (in ticks) the totem ticks                                                            | 4                 |
| HorizontalRadius | hRadius, hR | The horizontal radius entities will be hit in around the totem.                                 | 1.25              |
| VerticalRadius   | vRadius, vR | The vertical radius entities will be hit in around the totem.                                   | Horizontal Radius |
| Duration         | md          | The max duration (in ticks) the totem will persist.                                             | 200               |
| YOffset          | yo          | How high off the target the totem will spawn.                                                   | +1                |
| HitPlayers       | hp          | Whether can hit players. | false             |
| HitNonPlayers    | hnp         | Whether can hit non players. | false             |
| HitTarget        | ht          | Whether can hit skill target. | true              |
| HitTargetOnly    |             | Whether only can hit skill target | false             |

Examples
--------

```
  MyFirstTotem:
    Skills:
    - totem{ch=1;i=1;md=8;onTick=MFT_TICK} @self

  MFT_TICK:
    Skills:
    - damage{a=3}
```