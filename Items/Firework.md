This attribute is used to modify the firework effects of a firework or firework_charge items.
This attribute is required for every firework or firework_charge items.

### Format
```yml
ItemName:
  Id: material
  Firework:
    Colors:
    FadeColors:
    Flicker:
    Trail:
```

Breaking Down The Firework Configuration
---------------------------------------

### Colors
A list of primary colors to be added to the firework effect. The colors must be using RGB(red,green,blue) format.
```yml
# adds red(255,0,0), green(0,255,0), and blue(0,0,255) colors
# to the firework effect
example_item:
  Id: firework_charge
  Firework:
    Colors:
      - 255,0,0
      - 0,255,0
      - 0,0,255
```
### FadeColors
Similar to the [colors](/Items/Firework#Colors) option but adds the colors to the fade effect instead.
```yml
example_item:
  Id: firework_charge
  Firework:
    Colors:
      - 255,0,0
      - 0,255,0
      - 0,0,255
    FadeColors:
      - 255,0,255
      - 0,255,0
```
### Flicker
Whether the firework effect flickers
```yml
example_item:
  Id: firework_charge
  Firework:
    Flicker: true
```
### Trail
Whether the firework effect has a trail
```yml
example_item:
  Id: firework_charge
  Firework:
    Trail: true
```