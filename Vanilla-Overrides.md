Have you ever wanted to customize vanilla mobs too, instead of just making new ones? With Vanilla Overrides, it is possible!  

## What is an override?
A Vanilla Override is a special type of MythicMob. Like all other MythicMobs, it requires the normal mob syntax, apart from two exceptions:

  - **The [Internal Name](/Mobs/Mobs#internal_name) must be [the name of the type](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html) of a vanilla mob**  
  - **The mob does not need any [Type](/Mobs/Mobs#type) element**  

After having done that, the configured mob will override any vanilla entity whose type is that of the internal name of the Vanilla Override (for instance, if an override is called `Cow`, then all cow mobs will become that mythicmob). This works regardless of how the mob is spawned.

Apart from that, everything that works on a normal mythicmob can also be used in a Vanilla Override, so you can have, for instance, overrides with Disguises, with custom Damage Modifiers or with Skills!


## Examples
```yml
ZOMBIE:
  Options:
    PreventSunburn: true
```
```yml
CREEPER:
  Health: 100
  Display: '&bJohn'
  Disguise: Dolphin
  Options:
    MovementSpeed: 0.5
  Skills:
  - message{m="Oh no! I have died!"} @PlayersInRadius{r=30} ~onDeath
```