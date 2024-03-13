Basic Potion of Flight
--------------
* A simple potion with an enchantment glint that when consumed grants flight to the consumer for 1 minute.

For info on how the "basicflypot" skill is used, check [here](/examples/Consumable-Skills#drink-flight-potion-skill).

```yaml
basicflypot:
  Id: potion
  Display: '&f&lBasic&6 Potion of &b&lFlight&r'
  Options:
    Color: 89,255,230
  Lore:
  - '&9Flight (1:00)'
  Enchantments:
  - MENDING
  Hide:
  - ENCHANTS
  Skills:
  - skill{s=basicflypot} ~onConsume
```