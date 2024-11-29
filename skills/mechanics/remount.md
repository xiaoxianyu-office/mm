## Description
Causes the casting mob to remount the mob it spawned riding.

This move won't work if the rider's mount has despawned or is
killed.


## Attributes
> *This mechanic has no attributes*


## Examples
This example is a Mythic Mob named Rider, riding a Horse. When damaged,
the Rider dismounts the horse. When right clicked, the Rider will get
back onto the horse.
```yaml
Rider:
  Type: skeleton
  Display: 'Rider'
  Health: 12
  Mount: TestHorse
  Skills:
  - dismount ~onDamaged
  - remount ~onInteract
TestHorse:
  Type: horse
  Display: 'Test Horse'
  Health: 20
```


<!--TAGS-->
<!--tag:Mount-->