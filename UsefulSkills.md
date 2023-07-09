The following is a list of Skills that might result to be of use

Table of contents:

[[_TOC_]]



## Mobs



## Skills



## Items



## Drops & DropTables

### Multiple Drops
<details><summary>Let every player that took part in the fight receive a drop</summary>
<br>
This can be done by enabling the mob's [ThreatTable Module](/Mobs/ThreatTables) and by executing the following mechanic when the mob dies:  
<br>

```yaml
  Skills:
  - dropitem{i=droptable_name} @ThreatTablePlayers ~onDeath
```

In this manner, the mob will drop the droptable named `droptable_name` to every player in the mob Threat Table, effectively dropping it to every player that engaged the mob in combat
</details>

<details><summary>Let only the X players who dealt the most damage receive a drop</summary>
<br>
This can be done by enabling the mob's [ThreatTable Module](/Mobs/ThreatTables) and by executing the following mechanic when the mob dies:  

```yaml
  Skills:
  - dropitem{i=droptable_name} @ThreatTablePlayers{limit=X;sort=HIGHEST_THREAT} ~onDeath
```

Where X is the number of top players you want being able to receive the drop.

While this method is not necessarily precise (threat can decay, among other things) it's extremely simple to implement and the precision is in an acceptable range
</details>

### Specific Drops
<details><summary>Let only the player who dealt the most damage receive a drop</summary>
<br>
This can be done by enabling the mob's [ThreatTable Module](/Mobs/ThreatTables) and by executing the following mechanic when the mob dies:  

```yaml
  Skills:
  - dropitem{i=droptable_name} @ThreatTablePlayers{limit=1;sort=HIGHEST_THREAT} ~onDeath
```

While this method is not necessarily precise (threat can decay, among other things) it's extremely simple to implement and the precision is in an acceptable range
</details>