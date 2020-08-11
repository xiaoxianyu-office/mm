Mechanic: Feed
--------------

<img src="https://giant.gfycat.com/ColorfulSharpBeauceron.gif" width="400" height="50" alt="https://giant.gfycat.com/ColorfulSharpBeauceron.gif" />
  
Feeds the targeted player.  
Doesn't work for other mobs.

### Attributes

| Attribute  | Aliases | Description                         | Default |
|------------|---------|-------------------------------------|---------|
| amount     | a       | The amount of hunger to restore     | 1       |
| saturation | s       | The amount of saturation to restore | 0       |
| overfeed   | o,of    | Whether or not to overfeed          | false   |

**Note:**  
1 amount is half a food unit.  
Overfeeding means excess food is converted into saturation.  
Read more about
[hunger](https://minecraft.gamepedia.com/Hunger#Saturation) here!

  

### Examples

This skill feeds the player 10 hunger (or 5 drumsticks).

    Skills:
    - feed{amount=10;} @trigger ~onInteract
