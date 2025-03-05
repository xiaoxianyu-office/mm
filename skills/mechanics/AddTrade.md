## Description
Changes the trades of a villager.  
The villager will become a nitwit if it doesn't have any profession assigned when using this mechanic.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| action    | mode, m   | The action to perform. Can be `ADD`, `REMOVE`,`REPLACE`              | ADD<!--type:AddTrade_Action--> |
| slot      | s , index | The slot to be selected for the action. Slot starts at 0, so if a villager has 3 trades, the middle trade would be slot 1                                                       | 0       |
| ingredient| item, ingredient1, item1, i, i1 | The first ingredient                           | STONE<!--type:Item-->|
|ingredient2| item2, i2 | The second ingredient                                                |         |
| result    | r         | The result item of the trade                                         | STONE<!--type:Item-->|
| maxUses   | uses, u   | The uses of the trade                                                |<Max Int>|
| experienceReward | expReward, exp, dropExp | If the trade should drop experience             | false   |
| villagerExp | villExp, vexp | The amount of experience to give to the villager upon successful trade            | 0   |
| priceMultiplier|multiplier|The multiplier for the price when the player has made the villager angry |0 |
| demand    | d         | The demand of the trade                                              | 1       |
| specialPrice | special| The special price for when the villager is friendly to the player (player reputation or hero of the village effect)                                                      | 1       |
| ignoreDiscounts | discounts | If the discounts should be ignored                             | false   |


## Examples
```yaml
TestVillager:
  Type: Villager
  Display: 'OwO'
  Skills:
  - addTrade{item=DIAMOND 1;item2=EMERALD 2;result=IRON_INGOT 3;expReward=True;villExp=999;multiplier=0} @self ~onDamaged
  - addTrade{action=REPLACE;slot=1;item=DIRT 1;item2=COAL 2;result=DIAMOND_BLOCK 3;expReward=True;villExp=999;multiplier=0} @self ~onSignal:rev
```


## Aliases
- [x] setTrade
- [x] removeTrade
- [x] replaceTrade