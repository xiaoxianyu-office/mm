
**Aliases**: `effect:playanimation`, `e:playanimation`

**Description:**

Forces the entity to play an animation

Attributes
---------

| Attribute | Aliases | Description | Value |
|-----------|---------|-------------|-------|
| animation | a, effect, e | The animation to play | 1 |
| audience  | | The audience of the effect | world |

Animations
----------
|ID|	Animation|
|-------|--------|
|0|	Swing main arm|
|1|	Take damage|
|2|	Leave bed|
|3|	Swing offhand|
|4|	Critical effect|
|5|	Magic critical effect|


**Examples:**

```
- playanimation{a=1;audience=World} @Self
```