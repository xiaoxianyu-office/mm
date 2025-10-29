> [!important]
> This is something important you should know.


The following is a list of the implemented particles, associated with their DataType group. Based on the DataType they have, the attributes that can be used with them change accordingly.

**The most up to date version of this list is always going to be in the spigot Javadoc located [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html)**

- [DataTypes](#datatypes)
  - [ItemStack](#itemstack)
  - [BlockData](#blockdata)
  - [MaterialData](#materialdata)
  - [DustOptions](#dustoptions)
  - [DustTransition](#dusttransition)
- [Particles](#particles)

# DataTypes

## ItemStack
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m         | The material the particle will be based on                           | STONE   |


## BlockData
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m         | The material the particle will be based on                           | STONE   |

```yaml
  - effect:particles{particle=block_crack;material=COBBLESTONE}
```

## MaterialData
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m         | The material the particle will be based on                           | STONE   |

## DustOptions
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| color     | c         | The color of the particle                                            | #FF0000 |
| size      |           | The size of the particle                                             | 1       |

## DustTransition
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| color     | c, color1, c1, fromcolor, fc | The color the particles starts as                 | #FF0000 |
| color2    | c2, tocolor, tc | The color the particles transitions to                         | #0000FF |
| size      |           | The size of the particle                                             | 1       |

##
# Particles


| Ash | Block Crack |   |   |
|:---:|:-----------:|:-:|:-:|
| <a href="/skills/mechanics/Particle/Particle-Types/Ash"><img src="https://imgur.com/ggCYoIB.gif"></a>       | <a href="/skills/mechanics/Particle/Particle-Types/BlockCrack"><img src="https://imgur.com/bHpnok7.gif"></a>                                                                                                      |



### ash
![ash](https://imgur.com/ggCYoIB.gif)

##
### block_crack
![block_crack](https://imgur.com/bHpnok7.gif)
### [BlockData](#blockdata)
### Aliases
- [x] block
- [x] blockcrack

##
### block_dust
![block_crack](https://imgur.com/oHIBddK.gif)
### [BlockData](#blockdata)
### Aliases
- [x] dust
- [x] blockdust

##
### shriek
![image](https://imgur.com/eSmLMUL.gif)
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| rotation  | rot, r    | the rotation of the particle                                         | 0       |

##
### sculk_charge
![image](https://example.org/)
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| rotation  | rot, r    | the rotation of the particle                                         | 0       |
### Aliases
- [x] sculkcharge