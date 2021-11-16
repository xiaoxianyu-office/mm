**Description:** 

Stops a sound from playing from either the vanilla game or a resource pack for the targeted entity. A good list of sounds can be found [here](https://minecraft.fandom.com/wiki/Sounds.json#Sound_events). Use the “sound event” column.

---

**Attributes:**

| Attribute        | Alias | Description                                                   | Default Values |
| ---------------- | ----- | ------------------------------------------------------------- | -------------- |
| sound            | s     | Sound to stop playing                                            | entity.zombie.attack_iron_door           |
| soundcategory    | sc    | The category at which the sound is played, useful for resourcepacks | MASTER     |

A list of sound categories can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/SoundCategory.html).

---

**Examples:**

```
- stopsound{s=entity.enderman.scream} @PIR{r=10}
```