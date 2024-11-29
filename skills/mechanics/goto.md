## Description
Causes the mob to pathfind to a location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed     | s     | The movement speed modifier                                              | 1       |
| spreadH   | sh    | Amount of horizontal spread it can be away from the target its moving towards | 0  |
| spreadV   | sv    | Amount of vertical spread it can be away from the target its moving towards| 0     |


## Examples
```yml
  Skills:
  - goto{speedModifier=1;sh=5;sv=5} @owner
  - goto{speedModifier=1;sh=5;sv=5} @location{c=100,65,100}
```


## Aliases
- [x] pathto
- [x] navigateto


<!--TAGS-->
<!--tag:Movement-->
<!--tag:AI-->
