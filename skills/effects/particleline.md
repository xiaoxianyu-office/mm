**Description:** 

Creates a line of particles from the caster to the targeted entity or location. Extension of the [Particle Effect](/skills/effects/particles).

A list of particle types can be found [here](/skills/effects/particles/types).

---

**Attributes:**

This effect extends the general [Particle Effect](/skills/effects/particles) and uses all attributes from it.

Particle attributes are “per point” in this effect, so keeping 'amount' low is recommended.

| Attribute       | Alias    | Description                                         | Default Value |
| --------------- | -------- | --------------------------------------------------- | ------------- |
| distanceBetween | db       | The distance between each point in the line         | 0.25          |
| startYOffset    | syo      | Offset Y location of the starting point of the line | 0             |
| targetYOffset   | tyo      | Offset Y location of the target point of the line   | 0             |
| fromOrigin      | fo       | Whether to draw the line from the origin instead    | false         |
| xSpread         | xs       | Spread of particles on the x axis                   | 0             |
| ySpread         | ys       | Spread of particles on the y axis                   | 0             |
| zSpread         | zs       | Spread of particles on the z axis                   | 0             |
| zigzag          | zz       | Whether to draw the line to the target as a zigzag  | false         |
| zigzags         | zzs      | Amount of zigzags when using the zigzag option      | 10            |
| zigzagOffset    | zzo      | Offset of each zigzag                               | 0.2           |
| maxdistance     |          | The maximum distance the line can reach             | 256           |

---

**Examples:**

Example would draw a beam of fire from the origin to the target.

```
- effect:particleline{particle=flame;amount=1;fromOrigin=true} @target
```