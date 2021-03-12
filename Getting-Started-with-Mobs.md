MythicMobs is a highly customizable Mob creation plugin, where you can create your very own Mobs and Bosses based on YAML files. The level of complexity is up to you, make just a simple Zombie with armor or a massive Boss with minions, skills, custom drops and AI.

---
### Creating the file:
To create your first mob, navigate to the ``MythicMobs/Mobs`` folder and create a YAML file named ``tutorial_mob.yml``. (Do note, you can name it as you wish, but for sake of simplicity we will be using this file name on this tutorial.)

### Setting up basics:
Now that you have the mob file, lets start by populating it with your very own mob:
```

tutorial_pirate:
  # Basic part of a mob, this must be an alpha numeric, unique value as its how the mob is identified by the plugin.

  Type: ZOMBIE
  # Base mob type, must be a valid Minecraft Entity.

  Display: '&ePirate'
  # A String that will be used as the mob display name, can include color codes.

  Health: 100
  # Base Mob health.
  Damage: 10
  # Base Mob damage.

  Equipment:
  - IRON_SWORD HAND
  - SHIELD OFFHAND
  # The equipment that the mob uses, in this current setup, it equips an Iron Sword on the Main Hand and a Shield on the Offhand. 
  # Check Equipment for more info: https://git.mythiccraft.io/mythiccraft/MythicMobs/-/wikis/Mobs/Equipment

  Options:
  # Customization Options for mobs:
  # More options on: https://git.mythiccraft.io/mythiccraft/MythicMobs/-/wikis/Mobs/Options
    AlwaysShowName: true
    # - If true, always show the display name as nametag.
    PreventOtherDrops: true
    # - If true, disable vanilla drops.
    PreventSunburn: true
    # - If true, the mob won't burn in sunlight.

  Faction: PIRATE
  # Sets the mob faction, useful for AI and combat. 

  Skills:
  - message{msg="I will crush your bones!"} @PIR{r=10} ~onSpawn
  - sound{s=entity.player.attack.sweep} @Self ~onAttack
  - effect:particles{particle=sweep_attack;amount=1} @Self ~onAttack
  - message{msg="How could I be defeated?!"} @PIR{r=10} ~onDeath
``` 