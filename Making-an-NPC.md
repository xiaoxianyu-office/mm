Using a few basic tricks you can use MythicMobs to create highly versatile NPC's. The basic idea is to create a mob that has no AI/movement and doesn't despawn. We can then attach various mechanics and skills to our NPC mob such as messages, commands, or any skill you can think of.

# Step 1 - Basic NPC

The first step is simply making your mob file, this can be anywhere, for this example we'll make a NPC subfolder.

Using the below mob as a base, we can make a simple NPC that just stands still. We are using LibsDisguises to make the mob look like a player.

`plugins/MythicMobs/Mobs/NPC/Steve.yml`
```yaml
NPC_Steve:
  Type: ARMOR_STAND
  Display: 'Steve'
  Disguise: Player Steve setDynamicName true
  Options:
    Silent: true
    AlwaysShowName: true
    Collidable: false
    Despawn: persistent
  Skills:
  - cancelevent{sync=true} @self ~onDamaged
```

- `NPC_Steve` This is what you'll use to spawn your NPC. /mm m spawn NPC_Steve
- `Type: ARMOR_STAND` You can use whatever you like but we'll be using armor stand since it has no AI, no sound etc.
- `Display: 'Steve'` This is what will appear above your NPC's head.
- `Disguise: Player Steve setDynamicName true` This is what makes our NPC look like a player. You can replace "Steve" with whatever player name you want. You must keep the setDynamicName as true so the NPC can use the Display setting. For more information about using custom skins [read here](Mobs/Disguises)
- `AlwaysShowName: true` This makes the nameplate show above your NPC.
- `Collidable: false` This stops the NPC from being pushed around.
- `Despawn: persistent` This will keep your NPC spawned on reloads, restarts and chunk unloads.

For the skills we are using a cancelevent onDamaged to stop the mob from taking any damage. We are using a skill rather than Invincible: true as an option as this will prevent *all* damage sources including skills or other plugins.

# Step 2 - Adding messages and commands

You can add messages or commands to your NPC using the [Message](Skills/mechanics/message) and [Command](Skills/mechanics/command) mechanics. For this guide we will be using @trigger and onInteract which will show the message or run the command for a user who right clicks the NPC. When you are testing make sure you're in SURVIVAL mode as creative mode players wont be targetable.

### Message
```yaml
  Skills:
  - cancelevent{sync=true} @self ~onDamaged
  - message{m=&bWelcome to Hypixel &a<trigger.name>&b!;cd=3} @trigger ~onInteract
```

### Commands
This example will open a menu from DeluxeMenus for the player who right clicks the NPC.
```yaml
  Skills:
  - cancelevent{sync=true} @self ~onDamaged
  - command{c="dm open shops-blocks <trigger.name>"} @trigger ~onInteract
```

You can add as many skills or mechanics as you like to your NPC, not just messages and commands. You can run any mechanic and any metaskill.


# Step 3 - ModelEngine (Optional)

If you want your NPC to use a ModelEngine model we can remove the disguise line and instead use 2 skills to apply a model to it. We will be using onSpawn and onLoad to make sure the model is always applied to the mob even after restarts. 

You will also need to add a nametag bone to your models to display the name above them. You can do this by opening your model in Blockbench and creating an empty bone and calling it `tag_name`, then upload the newly edited model to your Blueprints folder and use `/meg reload`.

 `plugins/MythicMobs/Mobs/NPC/Steve.yml`
```yaml
NPC_Steve:
  Type: ARMOR_STAND
  Display: 'Steve'
  Options:
    Silent: true
    AlwaysShowName: true
    Collidable: false
    Despawn: persistent
  Skills:
  - model{m=SteveModel;n=name} @self ~onSpawn
  - model{m=SteveModel;n=name} @self ~onLoad
  - cancelevent{sync=true} @self ~onDamaged
```

With the model mechanic the attributes are
- `m=SteveModel` This is where the name of your model goes, for example we have `plugins/ModelEngine/Blueprints/SteveModel.bbmodel`
- `n=name` This is the name of our nametag bone we created.

# Step 4 - Spawning the NPC

You can now use `/mm reload` to reload the modified files and add your NPC into the server. Simply stand where you want the NPC to be and use `/mm m spawn NPC_Steve`.

You now have a NPC created by MythicMobs.