While a great deal of mob types can be used in MythicMobs, each one of them can have its quirks, and it is needed for every configurator to be aware of those quirks in order to minimize the damage they might cause.  

The following is a list of every discovered quirk that has been currently discovered. The more mainstream and discoverable problems will not be covered at this time, and only the niche ones will be treated. If you discover any other, let us know on our [Discord](https://discord.com/invite/K3tqXfT)

[[_TOC_]]

## All Zombies
Can spawn as leaders, having several times the amount of configured health.  

## ARMOR_STAND
Does not get targeted by default by multi entity targeters, and a [specific filter](Skills/Targeters#target-filters) must be used.  

## AXOLOTL
Can be Bucketed. Defend against this by using a [onBucket](Skills/Triggers#onbucket) trigger

## BEE
When allowed to randomfly, it will enter placed beehives and pollinate flowers.  
No definitive answer exists, apart from clearing its AI and building a new one.  

## BLAZE
Can be damaged by water, snowballs and the like. Use a [Damage Modifier](Mobs/DamageModifiers) in order to prevent this.  

## CAT
Scares Creepers and Phantoms away

## CHICKEN
Can lay eggs and is hunted by other animals.  
For the "egg problem", use the [Jockey Option](Mobs/Options#jockey).  

## COW
Can me milked.  

## ENDER_DRAGON
Has an hardcoded ai.

## ENDERMAN 
Avoids projectiles and is damaged by water.

## ENDERMITE
Aggroes Endermen.  

## Fox 
Have a unique attack pattern, can be useful but also problematic.

## GHAST
Can be one-shotted by a fireball.

## GIANT
Has an hardcoded ai.

## IRON_GOLEM
Can be healed via the use of iron ingots and get aggroed by default by most hostile mobs.

## PARROT
Can be one-shotted by a cookie.
<!-- Hello Toro! -->

## PHANTOM
Has an hardcoded ai.

## PIGLIN
Has an hardcoded aggro priority