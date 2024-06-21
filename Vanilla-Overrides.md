<!-- Can't believe Lxlp deleted my vanilla mobs page just so he could be the one to add it to the wiki :( -->

<!-- You better start to believe it! This my world (wiki) conquest! And it is only just beginning!  -->

<!-- "Oh, I must say, your ambition is as grand as your imagination! But let's be real here, I'm not just a spectator in this so-called 'world conquest' of yours. I'm an unstoppable force, and if you think you can handle the storm I bring, then I'm more than happy to watch your dreams shatter like fragile glass. Best of luck, you'll need it!" 🌪️ -->
<!-- Yeah, I got ChatGPT to write this -->

<!-- Foolish mortal! To think that a mere AI could overtake me! BLASPHEMOUS! You will be annihilated by your very own kind! LASER EYES, ATTACK! -->

<!-- shut up -->

<!-- I must hold the title of last edited by at all times -->

<!-- MUAHAHAHAHAH! I HAVE RETURNED!!!! -->

<!-- I will erase pasta and pizza from the world. Italy will fall. -->

Have you ever wanted to customize vanilla mobs too, instead of just making new ones? With Vanilla Overrides, it is possible!  

## What is an override?
A Vanilla Override is a special type of MythicMob. Like all other MythicMobs, it requires the normal mob syntax, apart from two exceptions:

  - **The [Internal Name](/Mobs/Mobs#internal_name) must be [the name of the type](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html) of a vanilla mob**  
  - **The mob does not need any [Type](/Mobs/Mobs#type) element**  

After having done that, the configured mob will override any vanilla entity whose type is that of the internal name of the Vanilla Override (for instance, if an override is called `Cow`, then all cow mobs will become that mythicmob). This works regardless of how the mob is spawned.

Apart from that, everything that works on a normal mythicmob can also be used in a Vanilla Override, so you can have, for instance, overrides with Disguises, with custom Damage Modifiers or with Skills!

By aware, though, that not all Mobs will become Vanilla Overrides: **mobs spawned via breeding of other mobs will not become overrides!**

## Examples
```yml
ZOMBIE:
  Options:
    PreventSunburn: true
```
##
```yml
CREEPER:
  Health: 100
  Display: '&bJohn'
  Disguise: Dolphin
  Options:
    MovementSpeed: 0.5
  Skills:
  - message{m="Oh no! I have died!"} @PlayersInRadius{r=30} ~onDeath
```
##
The following show an example of a PILLAGER override that still manages to correctly give out the bad omen effect, when a normal override would prevent this from happening
```yaml
PILLAGER:
  Skills:
  - skill{s=[
    - potion{t=BAD_OMEN;l=4;d=120000} ?~haspotioneffect{t=BAD_OMEN;l=3to4}
    - potion{t=BAD_OMEN;l=3;d=120000} ?~haspotioneffect{t=BAD_OMEN;l=2}
    - potion{t=BAD_OMEN;l=2;d=120000} ?~haspotioneffect{t=BAD_OMEN;l=1}
    - potion{t=BAD_OMEN;l=1;d=120000} ?~haspotioneffect{t=BAD_OMEN;l=0}
    - potion{t=BAD_OMEN;l=0;d=120000}
    ]} @trigger ~onDeath ?~isPlayer ?wearing{m=WHITE_BANNER}

```