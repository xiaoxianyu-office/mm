## Description 

Causes an explosion of temporary items at the target location.  
Unless otherwise specified with the `allowpickup` option, those items will be packets, only existing on the client of the players and not on the server.


## Attributes
| Attribute   | Alias     | Description                                        | Default Value |
| ----------- | --------- | -------------------------------------------------- | ------------- |
| item        | i         | The type of item can be a [Bukkit][] or Mythic item| iron_sword    |
| amount      | a         | How many items will render from the spray          | 10            |
| duration    | d         | How long (in ticks) the items will exist           | 20            |
| radius      | r         | The radius/spread the items will start in          | 0             |
| velocity    | v,force,f | The velocity of the items                          | 1             |
| yVelocity   | yv        | The Y velocity of the items                        | velocity      |
| yOffset     | yo        | The Y offset the items will start at               | 1             |
| allowpickup | ap        | If the itemspray items will be real items, enabling players to pick them up | false         |


## Examples

```
- effect:itemspray{item=iron_sword;amount=20;velocity=5;d=100} @self
```


  [Bukkit]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html