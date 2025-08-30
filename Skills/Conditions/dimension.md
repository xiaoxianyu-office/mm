## Description
Checks if the target is within a certain dimension.  
A list of valid dimensions can be found in the [Spigot Enviroment javadoc](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/World.Environment.html).


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| dimension | d, environment, env | A list of dimensions to check                              | THE_END<!--type:WorldEnviroment--><!--list--> |


## Examples
```yaml
  Conditions:
  - dimension{d=NORMAL} true
```


## Aliases
- [x] environment