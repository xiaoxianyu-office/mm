# RandomSpawns not working

- Check out the `Chance` of the randomspawn: if it's too low, that might be the issue, so bring it to `1` in order to check if that was the issue. If it was not, continue with the steps below without changing it back until the issue is solved.
- Check the world difficulty: if you are trying to spawn an hostile mob type, it shouldn't be peaceful!
- Remove **any limitations**, such as `biome` and `conditions`, then see if it works
- Check if there is any mispelled word anywhere, such as: 
    - the mob internal name
    - the world name
- If the RandomSpawn starts to work after deleting all conditions, start to add them back one by one, and see which one(s) caused the issue in the first place. If you are unable to understand why the conditions thus found are problematic, ask for help over our [discord]
- If the randomspawn is still not working, continue debugging by taking the actions listed below, based on the randomspawn's `Action`

### ADD Action
- Make sure the plugin's spawning configurations are correctly set
  - (Below MM 5.6.1): the config file is located at: `/MythicMobs/config.yml`
  - (MM 5.6.1 or above) the config file is located at: `/MythicMobs/config/config-spawning.yml`
- Make sure you have enabled `GeneraSpawnPoints` in the config file, or else the ADD action will not work
- Make sure you are in survival or adventure mode, as other gamemodes will not work
- If all of the above fails, ask for help over our [discord]

### REPLACE Action
- Check the world difficulty: it shouldn't be peaceful! 
- Make sure the world can spawn monsters naturally (For instace, by making sure that the `doMobSpawning` gamerule is set to `true` and other such things).
- Check region([World Guard](https://dev.bukkit.org/projects/worldguard), [Grief Defender](https://www.spigotmc.org/resources/1-12-2-1-20-4-griefdefender-claim-plugin-grief-prevention-protection.68900/) and so on) [flags](https://worldguard.enginehub.org/en/latest/regions/flags/#mobs-fire-and-explosions) to see if the region has any [flag which blocks mob spawning](https://worldguard.enginehub.org/en/latest/regions/flags/#mobs-fire-and-explosions)


<!-- LINKS -->
[discord]: https://www.mythiccraft.io/discord