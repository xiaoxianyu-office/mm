Effect: Particles
----

Creates a particle effect at the targeted entity or location.

A list of particle types can be found [here](/skills/effects/particles/types). 

[All of the spigot particle effects listed in the javadocs should be acceptable as well.](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html)

Added in 4.11: 
* Added dir=x,y,z option to particle effects to specify directional vector
* Added audience=\[world/target/caster\] options to all particle effects

Added in 4.12 (Premium Only!):
* Added special type particle=mob on all particle effects
* You can then specify a MythicMob using mob=\[type\]
* This is a hacky way for you to use mobs as "particles" in effects using no-tick ArmorStands wearing models or using font characters. You can use things other than ArmorStands if you want, but we don't recommend it for performance.

### Attributes
----

#### General Attributes

| Attribute  | Aliases | Description | Default Value |
| ------ | ------ | ------ | ------ |
| particle  | p  | The particle type to use. See list here.  | reddust |
| material | m | Block or Item to use with block_crack or item_crack respectively |
| mob |   | The entity to spawn as the particle. Cannot be the original entity |
| amount | a | The number of particles to create | 10    |
| hSpread | hs  | The horizontal spread of the particles | 0     |
| vSpread | vs  | The vertical spread of the particles | 0     |
| speed | s   | The “speed” of the particles | 0 |
| yOffset | y   | The Y offset of the particles from the target | 0 |
| viewDistance | vd  | The distance the particles are rendered | 128   |
| Size | | The size of the particles displayed | 1 |
| color | c | [(1)](/wikis/skills/effects/particles "only works on colorable particle types like “reddust”")[(2)](/wikis/skills/effects/particles "color must be provided in hex-code") The color of the particle |  |
| fromorigin |  |  | false |
| directional | d | Does the particle use directional travel | false | 
| directionReversed | | Reverses the direction of the particles. | false | 
| direction | dir | Specifies a vector for the particles to move towards. | 0,0,0 (x,y,z) | 

#### Entity-Only Attributes

| Attribute       | Aliases  | Description | Default Value |
|-----------------|----------|-------------|---------------|
| useEyeLocation | uel | (true/false) Whether to base the particles on the entity's eyes | false |
| forwardOffset   |  | The forward-offset from the targeted entity,doesn'n work when set directional to true | 0 |
| sideOffset | so | The side-offset from the targeted entity,doesn'n work when set directional to true | 0 |

#### Dust_color_transition-Specific Attributes

| Attribute | Aliases | Description                            |
|-----------|---------|----------------------------------------|
| color1    |         | The color the particles starts as      |
| color2    |         | The color the particles transitions to |


#### Particle Colors

As of MythicMobs version 2.3, some particles effects (mobSpell, mobSpellAmbient, and reddust) can be colored by using an additional “color=hexcode” argument. Hexcodes for coloring particles can be found here: [Hex Colors](http://www.color-hex.com/) From MM Version 2.5.0+ and Minecraft version 1.10 onwards, fallingdust also may use the color option.

    - effect:particles{p=reddust;color=#FF00FF}

### Mob-Type Particles

This particle type will replace the spawned particle with the selected entity. The entity will act as a normal one, being able to attack, be hit, activate skills and so on. The entity will have no parent/owner relationship with the caster.

### Examples
----
    Skills:
    - effect:particles{particle=flame;amount=200;hS=1;vS=1;speed=5} @self
    - ...

    Skills:
    - effect:particles{particle=block;m=dirt;amount=100;hS=1;vS=1} @self
    - ...

    Skills:
    - particles{particle=flame;a=10;hs=0.3;vs=0.3;y=0.3;s=0.1125} @self
    - ...