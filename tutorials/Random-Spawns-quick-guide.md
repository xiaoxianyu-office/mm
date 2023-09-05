Step 1. Copy the example random spawns.

Step 2. Decide if you want to REPLACE a mob spawn or ADD a new spawn.

Step 3. If adding a new spawn point on top of vanilla spawns change every instance of "MobType:" to "Type:" and use the ADD action

Step 4. Change the "Type:" value to the internal name of your mob. (eg. Type: MyMob)

Step 5. Add the worlds into the "Worlds:" array (eg. "Worlds: world,world_nether")

Step 6. Set the biomes the same way as worlds. Use only biomes listed here https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/Biome.html
If using Datapack biomes prefix the world with the datapack name (Biomes: terralith:desert_spires,terralith:emerald_peaks)

Step 7. Set the spawn priority. Higher number overrides lower. Priority 50 will be chosen over priority 1 spawns.

Step 8. Set the chances of the spawn at the spawnpoint. 0.001 is low, 1 is max.

Step 9. Set the conditions for the spawn to occur in the "Conditions:" field.
```yaml
Conditions:
- day true
- raining false
```
You can use the conditions found in here:
https://git.mythiccraft.io/mythiccraft/MythicMobs/-/wikis/Skills/conditions

Step 10. Set the position type (Particularly if making sea mobs.) Options are LAND and SEA (Works with ADD action only)

Step 11. Set the level of the mob or set "UseWorldScaling: [true/false]"

Step 12. Test and adjust values where needed.

Step 13. Enjoy.