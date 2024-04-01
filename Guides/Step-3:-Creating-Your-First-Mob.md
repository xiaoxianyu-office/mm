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

# Items File
`/plugins/MythicMobs/Items/SkeletonKing.yml`

Now we will create the items our mob needs for its armor and weapon.

# Drops File
`/plugins/MythicMobs/DropTables/SkeletonKing.yml`

<!---
I am too tired I must sleep zzzzz I will finish tomorrow <3
---!>