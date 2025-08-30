## Description
Checks for a range of damage the entity took, if the skilltree originated from a [onDamaged Trigger](/Skills/Triggers/onDamaged) or an [onDamaged Aura](/skills/mechanics/ondamaged).


## Attributes

| Attribute | Aliases      | Description                                                       | Default |
|-----------|--------------|-------------------------------------------------------------------|---------|
| damageAmount | amount, a | Range of damage to check for                                      | >0      |


## Examples
```yaml
  Conditions:
  - damageamount{amount=>10} true
```