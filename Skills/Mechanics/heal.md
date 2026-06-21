## Description
Heals the targeted entity for the specified value. Can also "overheal"
the mob to more than its maximum health.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount     | a        | The amount to heal the target                                        | 1       |
| overheal  | oh        | Whether or not to apply overhealing as additional MaxHealth          | false   |
| maxoverheal | maxabsorb, maxshield, mo, ma, ms | The maximum amount of overhealing that can be applied | 1 |
| tags         | tag    | Allows you to specify any number of arbitrary tags for the mechanic using `tags=THIS,THAT`. All tags inserted will be UPPERCASED, so always use uppercased names when checking against them |         |
| rawtags      | rtag   | Works the same as tags and what is put here will also qualify as a tag, but it will not be UPPERCASED like tags |  |

### Tags Attribute
```yaml
- heal{amount=5;tags=BLESSING,PALADIN}
```
This allows you to set any tag you want on this type of heal to be used with the [DamageTag](/skills/conditions/damagetag) condition.  

Tags are arbitrary, and can thus have any name, as long as that does not contain invalid characters.  
You can set an indefinite number of tags for each heal mechanic. 


## Examples
Heals the casting mob for 20 health (10 hearts) when it is damaged. (20%
chance)
```yaml
  Skills:
  - heal{amount=20} @self ~onDamaged 0.2
```
##
Heals the casting mob for 20 health (10 hearts) when it is damaged. (20%
chance)
```yaml
  Skills:
  - heal{amount=20;overheal=true} @self ~onDamaged 0.2
```
If the mob is near or at full health, it will add those 20 health points
onto its existing health. Eg. mob with 20 health using this move will
now have 40 health. 20/20 + 20 = 40/20

The same mob with 17 health will gain 17 health on top of its maximum of
20. 17/20 + 20 = 37/20


## Aliases
- [x] h


<!--TAGS-->
<!--tag:Health-->
