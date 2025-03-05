## Description

Summons mobs of the given type around the target.

<!--
To utilize the summon mechanic in Mythic Mobs, you will need the following:

1. Minecraft: make sure you have a working installation of Minecraft Java Edition on your computer

  - ChatGPT, 16/05/2023, oil on canvas
-->

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t, mob, m| The type of mob to summon. Can be a Mythic Mob type or a regular entity type                                                                 | SKELETON<!--type:Mob-->|
| onSummon  | onsummonskill, then | The [metaskill] to execute on the summoned mobs            |<!--type:Metaskill-->|
| amount    | a         | The number of mobs to summon.                                        | 1       |
| level     | l         | The level of the mob being summoned                                  | 0       |
| yaw       |           | The yaw of the summoned entities. If not set, will inherit the caster's |      |
| pitch     |           | The pitch of the summoned entities. If not set, will inherit the caster's |    |
| usetargetyaw | uty    | Whether the yaw of the target location/entity should be used to set the yaw of the summoned entity, unless the `yaw` attribute is set                                         | false   |
| usetargetpitch | utp  | Whether the pitch of the target location/entity should be used to set the pitch of the summoned entity, unless the `pitch` attribute is set                                    | false   |
| radius    | r, noise, n| The radius around the target within which the mobs will be summoned | 0       |
| yRadius   | yr, ynoise, yn| Overrides the Y component of radius.                             | radius  |
| yRadiusUpOnly | yradiusonlyup, yruo, yu| Whether the Y spread should only go upward, not downward.                                                                                      | false   |
| velocity | v, force, f| The maximum initial velocity the mob will have once summoned, making the mob be propelled in a random direction                                                                | 0       |
| yvelocity| yv, yforce, yf | Same as velocity, but only applied to the y axis                 | velocity|
| onSurface | os, s     |(true/false) Whether the mobs should be spawned only on a solid block | false   |
| copyThreatTable | ctt | Whether the summoned mobs should copy the parent's threat table. Requires threat tables to be enabled on the summoned mob to function.                                   | false   |
| inheritThreatTable | itt     | Whether the summoned mobs should share a threat table with the parent. Requires threat tables to be enabled on the summoned mob to function.                          | false   |
| inheritFaction | if   | Whether the summoned mobs should have the same faction as the parent | true    |
| inheritdespawn | inheritdespawnoption, ido | Whether the summoned mob should inherit the caster's [Despawn Option](/Mobs/Options#despawn)                                                        | false   |
| summonerIsOwner | sio | Whether to set the summoner as the owner of the mob.                 | true    |
| summonerIsParent | sip| Whether to set the summoner as the parent of the mob.                | true    |


## Examples
This example would summon 5 wither skeletons around the target players.
```yaml
RaiseSkeletons:
  Skills:
  - summon{type=WITHER_SKELETON;amount=5;radius=4} @PIR{r=20}
```


## Aliases
- [x] spawnmobs
- [x] spawnmob
- [x] piratesummon


<!-- LINKS -->
[metaskill]: /Skills/Metaskills


<!--TAGS-->
<!--tag:Summon-->
<!--tag:Meta-Mechanic:Thenable-->