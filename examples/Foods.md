The Donut
--------------
* A cookie example item that uses a resource pack, [Mythic Crucible](https://git.lumine.io/mythiccraft/mythiccrucible), and [CustomModelData](https://mcmodels.net/how-to-tutorials/resource-pack-tutorials/what-is-custommodeldata-2/) to make it look like a donut. When consumed, it gives a short burst of the saturation potion effect and gives a small amount of saturation replenishment.

For info on how the "eatmeal" skill is used, check [here](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Consumable-Skills#eat-food-skill).

```yaml
donut:
  Id: COOKIE
  Display: 'Donut'
  Model: 1
  Lore:
  - '&fBasic Food Item'
  - '&eCan be eaten'
  Skills:
  - skill{s=eatmeal} ~onConsume
```
![image](../uploads/66cd302e11d6e8fe2cc4a20b26f7f2e4/image.png)


Netherite Candy
--------------
An example item that uses the [food](Items/Items#food) and [consumable](Items/Items#consumable) item components to make the normally non-edible item, edible. Using Mythic Mobs Free. 
```yaml
NetheriteCandy:
  Material: NETHERITE_SCRAP
  Display: 'Delicious Scraps'
  Consumable:
    ConsumeSeconds: 0.5
    HasParticles: true
    Animation: EAT
  Food:
    Nutrition: 20
    Saturation: 20
    CanAlwaysEat: true
```
![image](uploads/434a50c1df7835469c9eda2819f17ad0/image.png){width=368 height=111}