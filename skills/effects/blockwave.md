**Description:** 

Creates a wave of the specified blocks, with varying shapes, speeds and blocks.

Note that the blockwave effect will never actually change any blocks in the world and thus will never grief the environment in any way. The changes made this effect are purely cosmetic, no actual blocks are changed and everything will always return to its original state.

Added in 4.12:
- Added velocityX, velocityY, velocityZ, and ignoreAir options

---

**Attributes:**

| Attribute | Alias  | Description                              | Default Value |
| --------- | ------ | ---------------------------------------- | ------------- |
| material  | mat, m | The type of block used for the blockmask | null          |
| data      | dv     | The data value used for the material     | 0             |
| radius    | r      | The radius of the blockwave effect       | 0             |
| radiusy   | n      | The y radius of the blockwave effect     | 0             |
| duration  | d      | Duration of the effect in ticks          | 15            |
| shape     | s      | The shape of the effect (Sphere/Cube)    | sphere        |
| velocity  | v      | The speed of the effect                  | 0.2           |
| velocityh | vh     | The speed of the effect in the horizontal direction      |
| velocityx | vx     | The speed of the effect in the x (?) direction | 0       |
| velocityy | vy     | The speed of the effect in the y (?) direction | 0       |
| velocityz | vz     | The speed of the effect in the z (?) direction | 0       |
| noise     | n      | The noise of the effect                        | 0       |
| hidesource | hsb, hs | Hides the source block                       | true  |  

---

Material must be the corresponding Bukkit-material name if one is added. A list of possible materials is below:

https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html

If material is left blank, it will use whatever material type it is used on. 
Example: if you leave it blank and use it on a villager building, you will see the blocks of the building used in the blockwave. 

The data value is only needed for old minecraft server versions - For example: using data value 1 on dirt will create coarse dirt.

there are 20 ticks in 1 second, and setting duration to 0 will have an infinite duration. 

Sphere and Cube are the only shapes available.

---

**Examples:**

1. Creates a stone blockwave in a sphere shape starting at your self location.

```
- blockwave{duration=100;material=stone;radius=5;radiusY=5;velocity=10;shape=sphere} @selflocation
```