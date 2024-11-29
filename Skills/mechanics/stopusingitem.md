## Description
Stops the targeted living entity from using an item, i.e. blocking with a shield.
> If you want to do some sort of cooldown, try using this mechanic in an aura


## Attributes
> *This mechanic has no attributes*


## Examples
```yaml
Skills:
  # basic example
  - stopusingitem @NearestPlayer
  
  # with an aura to prevent the player from using a shield
  - aura{onTick=[ - stopusingitem ?isBlocking ];duration=500} @NearestPlayer
```


## Aliases
- [x] releaseitem


<!--TAGS-->
<!--tag:Item-->
