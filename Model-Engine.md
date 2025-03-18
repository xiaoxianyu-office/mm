### Modelengine Custom Models

**ModelEngine is dependent on the plugin [ModelEngine](https://www.spigotmc.org/resources/conxeptworks-model-engine%E2%80%94ultimate-entity-model-manager-1-14-1-16-5.79477/)  
and requires the use of a custom resource pack. [The most up to date documentation for ModelEngine can be found here](https://git.lumine.io/mythiccraft/model-engine-4/-/wikis/home).  
You can also join Mythic's own [support discord](https://discord.com/invite/K3tqXfT) should you need help with your models**

*Modelengine has a free trial for a few special models so you can try before you buy, and there is a free test model on their wiki. You will have to make, or buy, your own models.*

### Now that the technical mumbo-jumbo is over... Why use ModelEngine??

ModelEngine allows anyone with BlockBench to quickly and easily create their own custom models and hit boxes similar to what you would see in mod packs, all in a vanilla client, using armor stands and a resource pack.

It is generally advised to use the `PreventOtherDrops` and `silent` mob options to avoid weird drops or noises coming from your ModelEngine Monster

<!-- ![image](uploads/5862ab1f31634ae0211a3c226d834540/image.png) -->
![image](uploads/934d66a2973c6e2cabce6d87cc0033db/left.png)

### Mechanics

ModelEngine runs a few mechanics in order to apply to the mob.  

To apply the "kindletronjr" model to a mob you would use this in the skills section of the mob:  
`- model{mid=kindletronjr;n=false} @self ~onSpawn`  
To play an attack animation you have made, you would put this in the skills section of a mob:  
`- state{mid=kindletronjr;s=attack;} @self ~onAttack`

For a full list of attributes and mechanics please visit the ModelEngine wiki:
https://git.mythiccraft.io/mythiccraft/model-engine-4/-/wikis/home

### Example:

```yaml
KindletronJR:
  Type: SILVERFISH
  Health: 20
  Damage: 0
  Skills:
  - model{mid=kindletronjr} @self ~onSpawn
  - skill{s=KindletronJRInit;sync=true} @self ~onAttack
  Options:
    Silent: true
    MovementSpeed: 0.1
    MaxCombatDistance: 25
    PreventOtherDrops: true
    PreventBlockInfection: true
```

Alternatively, the following way of setting the model up is also available:
```yaml
KindletronJR:
  Type: SILVERFISH
  Health: 20
  Damage: 0
  Model:
    Id: kindletronjr
    ViewRadius: 64
    Drive: false
    DamageTint: true
  Skills:
  - skill{s=KindletronJRInit;sync=true} @self ~onAttack
  Options:
    Silent: true
    MovementSpeed: 0.1
    MaxCombatDistance: 25
    PreventOtherDrops: true
    PreventBlockInfection: true
```