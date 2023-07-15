As well as creating custom mobs you are able to control Vanilla mobs as if they are mythic mobs too. To replace a vanilla mob with a mythic mob simply create a mob with the vanilla mob as its internal ID.
You can use all the existing Mythic options to modify the mob, but you **cannot change the Type: of the mob.** If you want to make vanilla mobs look like another mob you must use a disguise (Requires LibsDisguises)

```yml
ZOMBIE:
  Options:
    PreventSunburn: true
```
You are able to use all Mythic features including adding skills and mechanics to vanilla mobs.
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

You can view a list of the vanilla mob names [on the Spigot docs here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html)