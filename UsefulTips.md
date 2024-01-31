The following is a list of Skills that might result to be of use

Table of contents:

[[_TOC_]]

## General Rules
- NEVER test ANYTHING while in creative mode
- Always read the wiki page of what you are using in depth
- Always keep your plugins updated
- Make sure you are on a supported version. You can check that by doing `/mm version`
- Using ChatGPT to get configurations is a *truly* bad idea. Don't do that. Ever.

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
    ]} @trigger ~onDeath ?~isPlayer ?wearing{m=WHITE_BANNER}
```
</details>


## Skills

### Chat Messages
<details><summary>I want to warn every player that a mob has spawned</summary>
The [Placeholders wiki page](/Skills/Placeholders#examples) contains one such example.
</details>


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



<details><summary>Let the top X players who dealt the most damage receive specific drops</summary>
<br>
This can be done by enabling the mob's [ThreatTable Module](/Mobs/ThreatTables) and by executing the following mechanic when the mob dies:  

```yaml
  Skills:
  - skill{s=[
    - skill{s=[
      - dropitem{i=droptable_name_1}
      - threat{mode=reset}
      ]} @ThreatTablePlayers{limit=1;sort=HIGHEST_THREAT}
    - skill{s=[
      - dropitem{i=droptable_name_2}
      - threat{mode=reset}
      ]} @ThreatTablePlayers{limit=1;sort=HIGHEST_THREAT}
    - skill{s=[
      - dropitem{i=droptable_name_3}
      - threat{mode=reset}
      ]} @ThreatTablePlayers{limit=1;sort=HIGHEST_THREAT}
    ]} ~onDeath
```

This way, the droptable `droptable_name_1` will be dropped to the player that dealt the most damage, `droptable_name_2` to the one that dealt the second most damage and so on.

This happens because every time the inline skill
```yaml
    - skill{s=[
      - dropitem{i=droptable_name_1}
      - threat{mode=reset}
      ]} @ThreatTablePlayers{limit=1;sort=HIGHEST_THREAT}
```
is called, a droptable is given to the top threat, and then the threat against that target is removed, making the "next in line" to be considered the top threat holder.  
So, in order to drop something specific to the drop 10 instead of the top 3, you just have to repeat that segment over and over.

If you have MythicMobs Premium, something like the following becomes possible
```yaml
  Skills:
  - skill{s=[
    - skill{s=[
      - dropitem{i=droptable_name_<skill.var.itr>}
      - threat{mode=reset}
      ]} @ThreatTablePlayers{limit=1;sort=HIGHEST_THREAT}
    ];repeat=X;repeatInterval=1} ~onDeath
```
would also work, with X being the number of players you want to give the reward with minus one (so for top 10, X would be 9) and each player is given a droptable named `droptable_name_Y`, where Y is their place in the "leaderboard" (so first place would receive droptable_name_1, second place droptable_name_2 and so on)

</details>



<details><summary>Drop items to the last player that hit the mob</summary>
<br>
In this case, you will need to set a variable on the mob every time it is hit only if the trigger is a Player. Then, onDeath, you can use a UUID targeter to drop a specific item to whoever the variable is memorizing. This way, even if the mob dies for some other causes (Fire damage, Fall damage etc.), a player will always be selected for the drop, and is, as such, far more stable than dropping an item onDeath to the trigger.  
 

```yaml
  Skills:
  - setvariable{var=caster.lastplayer;type=STRING;val=<trigger.uuid>} @self ~onDamaged ?~isPlayer
  - dropitem{...} @UUID{u="<caster.var.lastplayer>"} ~onDeath ?variableisset{var=caster.lastplayer}
```
</details>


## Spawning

### Random Spawns
<details><summary>Mobs with the ADD spawn action are not spawning</summary>
You must have enabled `GenerateSpawnPoints` in the plugin's config file.
You must not be in creative or spectator mode.
</details>