# [THIS PAGE HAS BEEN MOVED!](/Skills/Mechanics)

Effects mechanics are now part of the Mechanics wiki page!

<!--
Skill Effects (or effect mechanics) are a special type of mechanic
specifically designed to create special effects. These are called just
like any other [skill mechanic][] in your mob's Skill List, or you can
add them to your own skills and even combine them.

Most effects are able to target both Entities and Locations. You control
what your effect targets using a [Targeter][].


# THIS PAGE IS CURRENTLY BEING MOVED OVER TO THE MECHANICS ONE, SOME LINKS MAY BECOME TEMPORARILY BROKEN DURING THIS PROCESS


## Syntax
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
- `nearby`: every nearby player
- `tracked`: every player who's clients can render the caster
- `@Targeter`: every player that the targeter targets

> The default value is `nearby`

Of particular relevance is the `audience=@Targeter` attribute, that allows any entity targeter to be used as the audience of the effect
```yaml
    Skills:
    - effect:particles{particle=reddust;y=2;audience=@Owner} @self
```

## Effects
| Effect Mechanic      | Description                                                           |
|----------------------|-----------------------------------------------------------------------|
| [Atom][]             | Creates electron-esque orbitals.                                      |
| [BlackScreen][]     | Blacks out the target's screen for the duration                       |
| [BlockMask][]       | Temporarily masks a block as a different block                        |
| [BlockUnmask][]     | Unmasks blocks that have been masked                                  |
| [BlockWave][]       | Creates a wave of blocks at the target location                       |
| [BloodyScreen][]    | Makes the target's screen glow red                                    |
| [Ender][]            | Causes the "Ender" effect                                             |
| [EnderBeam][]       | Creates the enderbeam effects at the target (similar to End Crystals) |
| [Explosion][]        | Causes an explosion effect                                            |
| [Firework][]         | Causes a firework explosion (currently not working in most builds)    |
| [Flames][]           | Causes the Mob Spawner flame effect                                   |
| [Geyser][]           | Creates a "geyser" of water or lava                                   |
| [Glow][]             | Gives the target the glow effect with different colors (req. GlowAPI) |
| [GuardianBeam][]     | Draw a guardian beam between the origin and the target                |
| [ItemSpray][]       | Sprays temporary items around the target                              |
| [Lightning][]        | Causes a fake lightning strike                                        |
| [Particles][]        | Creates particle effects around the target                            |
| [ParticleBox][]     | Draws a box of particles around the target                            |
| [ParticleEquation][]    | Generates particles based on equations                            |
| [ParticleLine][]    | Draws a line of particle effects to the target                        |
| [ParticleLine Helix][]    | Draws a line based helix effect                                 |
| [ParticleLine Ring][]    | Draws a particle ring connected by lines                         |
| [ParticleOrbital][] | Draws orbiting particle effects around the target                     |
| [ParticleRing][]    | Draws a ring of particles around the target                           |
| [ParticleSphere][]  | Draws a sphere of particles around the target                         |
| [ParticleTornado][] | Draws a persistent "tornado" of particles at the target               |
| [PlayAnimation][]   | Forces the entity to play an animation                                |
| [Recoil][]           | Kicks the target's screen                                             |
| [Skybox][]           | Alters the target's skybox                                            |
| [Smoke][]            | Creates a puff of smoke                                               |
| [Smoke Swirl][]      | Creates a persistent "swirl" of smoke                                 |
| [Sound][]            | Plays a sound effect from both vanilla Minecraft and resource packs   |               
| [Spin][]             | Causes the mob to spin                                                |
| [StopSound][]        | Stops a sound effect from playing                                     |
| [ThunderLevel][]     | Creates a rainless storm for players client side (per Player)         |
| [TotemOfUndying][]   | Plays the effect of a player resurrecting                             |


  [skill mechanic]: /skills/mechanics/
  [Targeter]: /skills/targeters/
  [Atom]:  /skills/mechanics/atom
  [BlackScreen]: /skills/mechanics/blackscreen
  [BlockMask]: /skills/mechanics/blockmask
  [BlockUnmask]: /skills/mechanics/blockunmask
  [BlockWave]: /skills/mechanics/blockwave
  [BloodyScreen]: /skills/mechanics/bloodyscreen
  [Ender]: /skills/mechanics/ender
  [EnderBeam]: /skills/mechanics/enderbeam
  [Explosion]: /skills/mechanics/FakeExplosion
  [Firework]: /skills/effects/firework
  [Flames]: /skills/effects/flames
  [Geyser]: /skills/effects/geyser
  [Glow]: /skills/mechanics/glow
  [GuardianBeam]: /effects/guardianbeam
  [ItemSpray]: /skills/effects/itemspray
  [Lightning]: /skills/mechanics/FakeLightning
  [Particles]: /skills/mechanics/particle
  [ParticleBox]: /skills/effects/particlebox
  [ParticleEquation]: /skills/effects/particleequation
  [ParticleLine]: /skills/effects/particleline
  [ParticleLine Helix]: /skills/effects/particlelinehelix
  [ParticleLine Ring]: /skills/effects/particlelinering
  [ParticleOrbital]: /skills/effects/particleorbital
  [ParticleRing]: /skills/effects/particlering
  [ParticleSphere]: /skills/effects/particlesphere
  [ParticleTornado]: /skills/effects/particletornado
  [Recoil]: /skills/effects/recoil
  [Skybox]: /skills/effects/skybox
  [Smoke]: /skills/effects/smoke
  [Smoke Swirl]: /skills/effects/smokeswirl
  [Sound]: /skills/effects/sound
  [Spin]: /skills/effects/spin
  [StopSound]: /skills/effects/stopsound
  [ThunderLevel]: /skills/effects/thunderlevel
  [TotemOfUndying]: /skills/effects/totemOfUndying
  [Atom]: /skills/mechanics/atom
  [ParticleVortex]: /skills/effects/particlevortex
  [DNA]: /skills/effects/dna
  [PlayAnimation]: /skills/effects/playanimation
-->