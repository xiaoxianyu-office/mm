## Description
Heals the target entity for a percentage of its max-health. Like the
heal skill, can also overheal mobs by a percentage.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| multiplier | m, amount, a | The percentage to heal, refers to the targets max-health.<br>0.1 = 10%, 1 = 100% and so on                                                                                      | 0.1     |
| overheal   | oh       | Whether or not to apply overhealing as additional MaxHealth          | false   |
| maxoverheal | maxabsorb, maxshield, mo, ma, ms | The maximum amount of overhealing that can be applied | 0 |
| tags         | tag    | Allows you to specify any number of arbitrary tags for the mechanic using `tags=THIS,THAT`. All tags inserted will be UPPERCASED, so always use uppercased names when checking against them |         |
| rawtags      | rtag   | Works the same as tags and what is put here will also qualify as a tag, but it will not be UPPERCASED like tags |  |

### Tags Attribute
```yaml
- healpercent{amount=0.5;tags=BLESSING,PALADIN}
```
This allows you to set any tag you want on this type of heal to be used with the [DamageTag](/skills/conditions/damagetag) condition.  

Tags are arbitrary, and can thus have any name, as long as that does not contain invalid characters.  
You can set an indefinite number of tags for each healpercent mechanic. 


## Examples
This will make the casting mob heal for 20% of its health each time it
gets to attack.
```yaml
  Skills:
  - healpercent{m=0.2} @self ~onAttack
```


## Aliases
- [x] percentheal
- [x] hp


<!--TAGS-->
<!--tag:Health-->
