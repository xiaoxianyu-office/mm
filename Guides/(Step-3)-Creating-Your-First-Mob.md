Now that you know all the basics, how to use them and where to use them, we will create our very first mob!

We will be creating a simple mob, a skeleton king with a couple of basic skills and items.

# Mob File
`/plugins/MythicMobs/Mobs/SkeletonKing.yml`

The basic Mob, here we are giving our mob an Internal ID, Type, Display, Health and Damage.

The Internal ID of this mob will be `SkeletonKing` this must be unique to every mob, and cannot be the same as other mobs. We will use this to spawn the mob `/mm m spawn SkeletonKing`
```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  Display: '&6Skeleton King'
  Health: 500
  Damage: 10
```

Next, we will add some options to our mob.
- `AlwaysShowName: true` makes the mobs Display appear above its head
- `MovementSpeed: 0.2` changes how fast the mob walks around
- `MaxCombatDistance: 25` changes the amount of blocks players can fight the mob from
- `PreventOtherDrops: true` stops the mob type from dropping its vanilla drops
```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  Display: '&6Skeleton King'
  Health: 500
  Damage: 10
  Options:
    AlwaysShowName: true
    MovementSpeed: 0.2
    MaxCombatDistance: 25
    PreventOtherDrops: true
```

Now we will add some Equipment, this allows us to customize how our mob looks and what weapons it uses. The items we are using here consist of a vanilla pair of boots, and 2 Mythic Items which we will create in our Items File below.
```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  Display: '&6Skeleton King'
  Health: 500
  Damage: 10
  Options:
    AlwaysShowName: true
    MovementSpeed: 0.2
    MaxCombatDistance: 25
    PreventOtherDrops: true
  Equipment:
  - KingsCrown HEAD
  - IRON_BOOTS FEET
  - SkeletonKingSword HAND
```

Since we removed the vanilla drops from the mob, we will add our own. We will handle these drops with a DropTable which we will create below.
```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  Display: '&6Skeleton King'
  Health: 500
  Damage: 10
  Options:
    AlwaysShowName: true
    MovementSpeed: 0.2
    MaxCombatDistance: 25
    PreventOtherDrops: true
  Equipment:
  - KingsCrown HEAD
  - IRON_BOOTS FEET
  - SkeletonKingSword HAND
  Drops:
  - SkeletonKingDrops
```

And finally, we will add some skills to our mob to give it interesting abilities!

We are adding 2 mechanics and 2 MetaSkills to the mob, the MetaSkills will be created in the skills file below. Head to the [Mechanics](/Skills/Mechanics), [Targeters](/Skills/Targeters) and [Triggers](/Skills/Triggers) pages to see what the mechanic does!
```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  Display: '&6Skeleton King'
  Health: 500
  Damage: 10
  Options:
    AlwaysShowName: true
    MovementSpeed: 0.2
    MaxCombatDistance: 25
    PreventOtherDrops: true
  Equipment:
  - KingsCrown HEAD
  - IRON_BOOTS FEET
  - SkeletonKingSword HAND
  Drops:
  - SkeletonKingDrops
  Skills:
  - speak{m="None may challenge the Skeleton King!";cooldown=20} @PlayersInRadius{r=40} ~onCombat 0.2
  - speak{m="Ahahahahah! Die, <trigger.name>!"} @PlayersInRadius{r=40} ~onPlayerKill
  - skill{s=SummonSkeletons} @self 0.1
  - skill{s=SmashAttack} @target 0.2
```
By adding 0.2 and 0.1 after some of the mechanics, we are giving them a chance to execute, meaning they won't happen 100% of the time. The chance is out of 1 so 0.2 is a 20% chance.

# Skills File
`/plugins/MythicMobs/Skills/SkeletonKing.yml`

The skills file will contain the MetaSkills `SummonSkeletons` and `SmashAttack` which we used in our Mob file.

### SummonSkeletons
Our skill has an internal ID of `SummonSkeletons` which is what we will use when calling the skill, we are giving it a Cooldown of 15 seconds, meaning that once the skill is executed it can't happen again for that duration.

Mechanics:
- [message](/mechanics/message) We are sending a message to all players in a radius of 40 around the mob, informing them of the skeletons being spawned. We are using the caster.name placeholder which will get the Display setting from our mob, and the &co placeholder which will insert a : since that can mess up the syntax if used directly.
- [delay 20](/mechanics/delay) This adds a delay of 20 ticks (1 second) between the message and the next mechanic
- [summon](/mechanics/summon) We are summoning 2 basic skeleton mobs which will be placed randomly 5 blocks around the Skeleton King. The summon mechanic supports vanilla mobs (like we've used) or other MythicMobs using their Internal ID.
We are repeating the delay and summon mechanics which will spawn a total of 6 skeletons over the course of 3 seconds.

```yaml
SummonSkeletons:
  Cooldown: 15
  Skills:
  - message{m="<caster.name><&co> Arise, my minions!"} @PlayersInRadius{r=40}
  - delay 20
  - summon{mob=SKELETON;amount=2;radius=5} @Self
  - delay 20
  - summon{mob=SKELETON;amount=2;radius=5} @Self
  - delay 20
  - summon{mob=SKELETON;amount=2;radius=5} @Self
```
> Note that, to repeat a mechanic multiple times, you can also use the `repeat` and `repeatInterval` universal attributes
> So, the above metaskill can be rewritten as
> ```yaml
> SummonSkeletons:
>   Cooldown: 15
>   Skills:
>   - message{m="<caster.name><&co> Arise, my minions!"} @PlayersInRadius{r=40}
>   - delay 20
>   - summon{mob=SKELETON;amount=2;radius=5;repeat=2;repeatInterval=20} @Self
> ```

### SmashAttack
This skill causes the mob to teleport to its target, deals damage to the target and throwing them in the air.

We are using a condition to ensure that the target is within a set distance, if the target is too far, then the skill won't execute.
- [TargetWithin{d=25}]() Ensures the target is within 25 blocks of the mob

Mechanics:
- [message](/mechanics/message) We are showing all players in a 40 block radius a message warning of the attack
- [teleport](/mechanics/teleport) Teleporting the mob directly to the targeted player
- [sound](/mechanics/Sound) Playing an enderman teleport sound originating at the mobs location
- [delay](/mechanics/delay) Delaying the skill by 10 ticks
- [damage](/mechanics/damage) Dealing 5 damage directly to all players within 5 blocks of the mob, ignoring their armor
- [throw](/mechanics/throw) Throwing the players with velocity and Y velocity
- [fakeexplosion](/mechanics/FakeExplosion) Causing an explosion effect which does no damage and doesn't break blocks.
```yaml
SmashAttack:
  Cooldown: 8
  Conditions:
  - targetwithin{d=25}
  Skills:
  - message{cooldown=30;m="<mob.name><&co> Hahahah! I will crush you, fool!"} @PlayersInRadius{r=40}
  - teleport @target
  - sound{s=mob.endermen.portal;volume=1.0;pitch=0.5}
  - delay 10
  - damage{amount=5;ignorearmor=true} @PlayersInRadius{r=5}
  - throw{velocity=10;velocityY=5} @PlayersInRadius{r=5}
  - fakeexplosion @Self
```
# Items File
`/plugins/MythicMobs/Items/SkeletonKing.yml`

Now we will create the items our mob needs for its armor and weapon.

First we will create our sword. We will be giving it a Display and Lore which displays when you hover over the item in your inventory, and we will be giving it enchantments. The DAMAGE_ALL enchantment is the name for Sharpness. We are adding attributes to the sword which give the holder +10 health and 10% extra movement speed.

```yaml
SkeletonKingSword:
  Id: DIAMOND_SWORD
  Display: '&3Greatsword of the Skeleton King'
  Lore:
  - '&6A powerful sword used by'
  - '&6the King of Skeletons.'
  Enchantments:
  - DAMAGE_ALL:5
  - KNOCKBACK:2
  - FIRE_ASPECT:2
  Attributes:
    MainHand:
      Health: 10
      MovementSpeed: 0.1
```

Now we will create our crown, much like the sword above we are giving it a Display, Lore, Enchantments and Attributes. We are also adding 2 Hide flags, this will hide the Attributes and Enchants from being displayed in the items lore.

```yaml
KingsCrown:
  Id: GOLDEN_HELMET
  Display: '&dCrown of the King'
  Lore:
  - '&6A kingly crowl that grants'
  - '&6the wearer unwavering power!'
  Enchantments:
  - PROTECTION_ENVIRONMENTAL:2
  - PROTECTION_PROJECTILE:2
  - PROTECTION_FIRE:2
  - PROTECTION_EXPLOSIONS:2
  Hide:
  - ATTRIBUTES
  - ENCHANTS
  Attributes:
    Head:
      Health: 10
      KnockbackResistance: 10
```

# Drops File
`/plugins/MythicMobs/DropTables/SkeletonKing.yml`

For our drops we are creating 2 drop tables, and making the first one drop the 2nd one. We are using a condition to make sure that items from the 2nd drop table only drop if the mob dies at night.

The format for drops is `<Drop Type> <Amount> <Chance>` so in our first drop table we are dropping 1 of the SkeletonKingItemDrops droptable 100% of the time and dropping a random amount of EXP between 100 and 150. In the SkeletonKingItemDrops we are giving the Crown a 1% Chance of dropping and the Sword a 10% chance of dropping. 

We are using MinItems and MaxItems to indicate how many items we want the droptable to drop altogether, it will drop either 1 or 2 drops from the list. This is not the total amount of individual items, since the gold nuggets and diamonds have a range of items, they could drop 64 nuggets and 12 diamonds, which still fits into the MaxItems being 2.

```yaml
SkeletonKingDrops:
  Drops:
  - SkeletonKingItemDrops 1 1
  - experience 100-150 1
  
SkeletonKingItemDrops:
  Conditions:
  - night
  MinItems: 1
  MaxItems: 2
  Drops:
  - KingsCrown 1 0.01
  - SkeletonKingSword 0.1
  - GOLD_NUGGET 32-64 1
  - DIAMOND 1-12 0.8
```

# Testing
Now you have created all the files needed for our custom mob! The next thing to do is head in-game and use `/mm reload` to load the mob and its items into the server, then spawn it with `/mm m spawn SkeletonKing` and checking it works!

# Random Spawn File
`/plugins/MythicMobs/RandomSpawns/SkeletonKing.yml`

Now that you have your mob, you may want to make it spawn randomly in the world. We can setup a simple RandomSpawns file which will make that happen!

RandomSpawns are fairly easy to use, and you can find the information on creating them on their wiki page. 

For this guide we will be making a basic one which spawns our Skeleton King outside at night time. We will be using the REPLACE action which replaces a vanilla mob spawn with our custom mob, and giving it a condition to make it only replace Skeletons.

We are using a chance of `0.005` which will give the spawn a 0.5% chance of replacing a skeleton, every time a skeleton spawns.

Make sure to replace `world` with the name of the world (or a list of worlds seperated by ,) you want the mob to spawn in.

```yaml
RandomSkeletonKing:
  Type: SkeletonKing
  Worlds: world
  Chance: 0.005
  Priority: 1
  Action: REPLACE
  Conditions:
  - outside true
  - night true
  - entitytype{t=SKELETON}
```

**[>> Step 4](/Guides/(Step-4)-Essential-Commands)**