Skill Effects
-------------

Skill Effects (or effect mechanics) are a special type of mechanic
specifically designed to create special effects. These are called just
like any other [skill mechanic][] in your mob's Skill List, or you can
add them to your own skills and even combine them.

Most effects are able to target both Entities and Locations. You control
what your effect targets using a [Targeter][].

### Syntax

A lot of effects don't have any options. To call them, you just call the
skill **effect:name**, for example:

```yaml
    Skills:
    - effect:flames @target
    - effect:lightning @self
    - effect:ender @PlayersInRadius{r=20}
    - effect:ender @PlayersInRadius{r=20}
    - effect:particles{particle=reddust;color=#EE22CC;amount=10;speed=1;hS=0.15;vS=.15;audience=Target} @target
```

### Audience 
Audience arguments can be used to display the effect only to a specific group of players, rather than the entire server, by using the `audience=<audience type>` attribute in an effect mechanic and specifying an audience type to use. This can be useful in preventing too many particles from being displayed to everyone unnecessarily, and can reduce client-side lag to some extent.

The audience types are:
- `self`/`caster`: the caster of the mechanic
- `nonSelfWorld`/`nonSelf`: every player in the world other than the caster of the mechanic
- `target`: the target of the mechanic
- `world`: every player in the world
- `@Targeter`: every player that the targeter targets

Of particular relevance is the `audience=@Targeter` attribute, that allows any entity targeter to be used as the audience of the effect
```yaml
    Skills:
    - effect:particles{particle=reddust;y=2;audience=@Owner} @self
```

### Effects

| Effect Mechanic      | Description                                                           |
|----------------------|-----------------------------------------------------------------------|
| [Atom][]             | Creates electron-esque orbitals.                       |
| [Black Screen][]     | Blacks out the target's screen for the duration                       |
| [Block Mask][]       | Temporarily masks a block as a different block                        |
| [Block Unmask][]     | Unmasks blocks that have been masked                                  |
| [Block Wave][]       | Creates a wave of blocks at the target location                       |
| [Bloody Screen][]    | Makes the target's screen glow red                                    |
| [Ender][]            | Causes the "Ender" effect                                             |
| [Ender Beam][]       | Creates the enderbeam effects at the target (similar to End Crystals)                           |
| [Explosion][]        | Causes an explosion effect                                            |
| [Firework][]         | Causes a firework explosion (currently not working in most builds)                 |
| [Flames][]           | Causes the Mob Spawner flame effect                                   |
| [Geyser][]           | Creates a "geyser" of water or lava                                   |
| [Glow][]             | Gives the target the glow effect with different colors (req. GlowAPI) |
| [GuardianBeam][]     | Draw a guardian beam between the origin and the target                |
| [Item Spray][]       | Sprays temporary items around the target                              |
| [Lightning][]        | Causes a fake lightning strike                                        |
| [Particles][]        | Creates particle effects around the target                            |
| [Particle Box][]     | Draws a box of particles around the target                            |
| [Particle Equation][]    | Generates particles based on equations                        |
| [Particle Line][]    | Draws a line of particle effects to the target                        |
| [Particle Line Helix][]    | Draws a line based helix effect                        |
| [Particle Line Ring][]    | Draws a particle ring connected by lines                        |
| [Particle Orbital][] | Draws orbiting particle effects around the target                     |
| [Particle Ring][]    | Draws a ring of particles around the target                           |
| [Particle Sphere][]  | Draws a sphere of particles around the target                         |
| [Particle Tornado][] | Draws a persistent "tornado" of particles at the target               |
| [Play Animation][]   | Forces the entity to play an animation                                |
| [Recoil][]           | Kicks the target's screen                                             |
| [Skybox][]           | Alters the target's skybox                                            |
| [Smoke][]            | Creates a puff of smoke                                               |
| [Smoke Swirl][]      | Creates a persistent "swirl" of smoke                                 |
| [Sound][]            | Plays a sound effect from both vanilla Minecraft and resource packs   |               
| [Spin][]             | Causes the mob to spin                                                |
| [StopSound][]        | Stops a sound effect from playing                                     |
| [SummonAreaEffectCloud][]        | Summons a cloud of particles at the target                                     |
| [ThunderLevel][]     | Creates a rainless storm for players client side (per Player)                           |
| [TotemOfUndying][]     | Plays the effect of a player resurrecting                           |

<!--
### EffectLib Effects

These effects require the plugin "EffectLib" to be installed to use.

**Note: EffectLib was dropped in MM ver 4.11, so the below effects no longer work.**

| Effect Mechanic     | Description                                           |
|---------------------|-------------------------------------------------------|
| [Atom][]            | Creates a representation of an atom around the target |
| [Particle Vortex][] | Draws a "vortex" of particles around the target       |
| [DNA][]             |                                                       |
Edit: (Dant35tra5t) Atom is working for some reason. Putting it in main list.
-->

  [skill mechanic]: /skills/mechanics/
  [Targeter]: /skills/targeters/
  [Atom]:  /skills/effects/atom
  [Black Screen]: /skills/effects/blackscreen
  [Block Mask]: /skills/effects/blockmask
  [Block Unmask]: /skills/effects/blockunmask
  [Block Wave]: /skills/effects/blockwave
  [Bloody Screen]: /skills/effects/bloodyscreen
  [Ender]: /skills/effects/ender
  [Ender Beam]: /skills/effects/enderbeam
  [Explosion]: /skills/effects/explosion
  [Firework]: /skills/effects/firework
  [Flames]: /skills/effects/flames
  [Geyser]: /skills/effects/geyser
  [Glow]: /skills/effects/glow
  [GuardianBeam]: /effects/guardianbeam
  [Item Spray]: /skills/effects/itemspray
  [Lightning]: /skills/effects/lightning
  [Particles]: /skills/effects/particles
  [Particle Box]: /skills/effects/particlebox
  [Particle Equation]: /skills/effects/particleequation
  [Particle Line]: /skills/effects/particleline
  [Particle Line Helix]: /skills/effects/particlelinehelix
  [Particle Line Ring]: /skills/effects/particlelinering
  [Particle Orbital]: /skills/effects/particleorbital
  [Particle Ring]: /skills/effects/particlering
  [Particle Sphere]: /skills/effects/particlesphere
  [Particle Tornado]: /skills/effects/particletornado
  [Recoil]: /skills/effects/recoil
  [Skybox]: /skills/effects/skybox
  [Smoke]: /skills/effects/smoke
  [Smoke Swirl]: /skills/effects/smokeswirl
  [Sound]: /skills/effects/sound
  [Spin]: /skills/effects/spin
  [StopSound]: /skills/effects/stopsound
  [SummonAreaEffectCloud]: /skills/effects/summonareaeffectcloud
  [ThunderLevel]: /skills/effects/thunderlevel
  [TotemOfUndying]: /skills/effects/totemOfUndying
  [Atom]: /skills/effects/atom
  [Particle Vortex]: /skills/effects/particlevortex
  [DNA]: /skills/effects/dna
  [Play Animation]: /skills/effects/playanimation