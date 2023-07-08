The following is a list of Skills that might result to be of use

Table of contents:

[[_TOC_]]



# Mobs
## TODO
# Skills
## TODO
# Items
## TODO
# Drops & DropTables
## Multiple Drops
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