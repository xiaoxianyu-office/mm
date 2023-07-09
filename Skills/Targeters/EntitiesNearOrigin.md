## Description
Targets all entities in the given radius around the origin of the metaskill.  
This targeter is an extension of the **[EntitiesInRadius Targeter](/Skills/Targeters/EntitiesInRadius)** and can, as such, **use any of its attributes**


## Attributes
>*This targeter has no unique attributes, but can use the [EntitiesInRadius](/Skills/Targeters/EntitiesInRadius)'s ones*


## Examples
In this example, when the created projectile ends for whatever reason, it will damage every living entity in a 2 block radius around itself
```yaml
  Skills:
  - projectile{...;
    onTick=[
      - effect:particles @origin
    ];
    onEnd=[
      - damage{a=10} @ENO{r=2}
    ]
    } @target
```


## Aliases
- [x] NearOrigin
- [x] ENO