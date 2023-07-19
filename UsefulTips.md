The following is a list of Skills that might result to be of use

Table of contents:

[[_TOC_]]



## Mobs

### Overrides
<details><summary>My PILLAGER override is not giving bad omen</summary>
<br>
This is a common issue. To fix this, consider adding the following skill to your PILLAGER mob override:  
 

```yaml
  Skills:
  - skill{s=[
    - potion{t=BAD_OMEN;l=4;d=120000} ?~haspotioneffect{t=BAD_OMEN;l=3to4}
    - potion{t=BAD_OMEN;l=3;d=120000} ?~haspotioneffect{t=BAD_OMEN;l=2}
    - potion{t=BAD_OMEN;l=2;d=120000} ?~haspotioneffect{t=BAD_OMEN;l=1}
    - potion{t=BAD_OMEN;l=1;d=120000} ?~haspotioneffect{t=BAD_OMEN;l=0}
    - potion{t=BAD_OMEN;l=0;d=120000}
    - command{c="say test"}
    ]} @trigger ~onDeath ?~isPlayer ?wearing{m=WHITE_BANNER}
```
</details>


## Skills



## Items



## Drops & DropTables

### Multiple Drops
<details><summary>Let every player that took part in the fight receive a drop</summary>
<br>
This can be done by enabling the mob's [ThreatTable Module](/Mobs/ThreatTables) and by executing the following mechanic when the mob dies:  
 

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

<details><summary>Drop items to the last player that hit the mob</summary>
<br>
In this case, you will need to set a variable on the mob every time it is hit only if the trigger is a Player. Then, onDeath, you can use a UUID targeter to drop a specific item to whoever the variable is memorizing. This way, even if the mob dies for some other causes (Fire damage, Fall damage etc.), a player will always be selected for the drop, and is, as such, far more stable than dropping an item onDeath to the trigger.  
 

```yaml
  Skills:
  - setvariable{var=caster.lastplayer;type=STRING;val=<trigger.uuid>} @self ~onDamaged ?~isPlayer
  - dropitem{...} @UUID{u="<caster.var.lastplayer>"} ~ronDeath ?variableisset{var=caster.lastplayer}
```
</details>