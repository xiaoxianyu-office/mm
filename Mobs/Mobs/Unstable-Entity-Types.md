While a great deal of entity types can be used in MythicMobs, each one of them can have its quirks, and it is needed for every configurator to be aware of those quirks in order to minimize the damage they might cause or, in general, to better use the entity.  

The following is a list of every quirk that has been currently discovered. The more mainstream and obvious problems will not be covered at this time, and only the niche ones will be treated. If you discover any other, let us know on our [Discord](https://discord.com/invite/K3tqXfT)

[[_TOC_]]

## Mobs by Group
### All Zombies
Can spawn as leaders, having several times the amount of configured health.  

### All passive animals
Could get aggroed by other entities.

### All breedable animals
They can usually be fed by some item and, subsequently, try to breed.  
This can be handled by intercepting the event [~onBreed](/Skills/Triggers/onBreed) (and then either cancelling it or some other mechanic) or completely prevented by using the [Age](/Mobs/Options#age) option

### Most bosses
Have an hardcoded ai or some other hardcoded features.

### Entities damaged by water
Affected entities include Enderman, Snowman and Blaze.  
The damage type in those instances if of the `DROWNING` type, and can thus be fully prevented by using a negative value for it as a [DamageModifier](/Mobs/DamageModifiers) or by using the following skill
```yaml
   - cancelevent{sync=true} ~ondamaged ?damagecause{c=drowning}
```

## Specific Mobs
### ARMOR_STAND
Does not get targeted by default by multi entity targeters, and a [specific filter](/Skills/Targeters#target-filters) must be used.  

### AXOLOTL
Can be Bucketed. Defend against this by using a [onBucket](/Skills/Triggers/onBucket) trigger

### BEE
When allowed to randomfly, it will enter placed beehives and pollinate flowers.  
No definitive answer exists, apart from clearing its AI and building a new one.  

### BLAZE
Can be damaged by water, snowballs and the like. Use a [Damage Modifier](/Mobs/DamageModifiers) in order to prevent this.  

### CAT
Scares Creepers and Phantoms away

### CHICKEN
Can lay eggs and is hunted by other animals.  
For the "egg problem", use the [Jockey Option](/Mobs/Options#jockey).  

### COW
Can be milked.  

### DROWNED
By default, it does not attack its target in the day if they are not in a water block. A [custom ai](/Mobs/Custom-AI) must be set up in order to remove this behavior

### ENDER_DRAGON
Has a hardcoded ai.

### ENDERMAN 
Avoids projectiles and is damaged by water.

### ENDERMITE
Draws aggro from Endermen.  

### FOX
Has an unique attack pattern, can be useful but also problematic.

### GHAST
Has a hardcoded ai.
Can be one-shotted by a fireball.

### GIANT
Has a hardcoded ai.

### IRON_GOLEM
Can be healed via the use of iron ingots and draws aggro by default from most hostile mobs.

### MAGMA_CUBE
Has a hardcoded ai.

### PARROT
Can be one-shotted by a cookie.

### PHANTOM
Has a hardcoded ai.

### PIGLIN
Has a hardcoded aggro priority

### PILLAGER
If, for any reason, a pillager loses his target while holding a charged crossbow, then it will freeze

### PUFFERFISH
Has very unique interactions and behaviors that may cause problems.

### RABBIT
Draws aggro from other neutral mobs, such as foxes.

### SKELETON
Draws aggro from wolves

### SLIME
Has a hardcoded ai.

### SQUID
Do not work with mechanics such as [lunge](/skills/mechanics/lunge) and [throw](/skills/mechanics/throw).  
This also applies to GLOW_SQUID

### VEX
Has a hardcoded ai.

### WARDEN
Has a hardcoded aggro system.

### WITHER
Has a hardcoded ai.

### WOLF
Can be healed via the use of specific items
Once it becomes "Tamed", the health resets.