## Description
The description of the mechanic: what it does, how it does it, and possible notes.

> **This is a [Paper-Only] mechanic!**

> **This is a [Premium-Only] mechanic!**


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| attribute1| alias1, alias2| The description of what the attributes does                 | default value|
| attribute2| alias3    | The description of what the attributes does                     | default value|
| attribute3|           | The description of what the attributes does                     | default value|
| attribute4|           |The description of what the attributes does **<[Premium-Only]>**|default value|
<!-- Optional, if an inheritance is in place -->
> This mechanic inherits every attribute of the [ExampleMechanic2](Wiki-Editors-Resources/ExampleMechanic2) mechanic
>> The `attribute4` attribute is defaulted at `0`
<!-- If inherited attributes have their default value changed> -->

<!-- If the mechanic does not have any attributes-->
> *This mechanic has no attributes*

### Attribute1 Attribute
A more in-depth explanation of what the attributes does, how it does it, what values are accepted and so on. Optional, only if necessary.


## Examples
A description of the example below.
```yaml
  Skills:
  - examplemechanic{attribute1=value1} @targeter
```
## <!-- Use ## to separate different examples -->
Another example:
```yaml
  Skills:
  - examplemechanic{attribute1=value1;attribute2=value2} @targeter
```


## Aliases
- [x] mechanic_alias_1
- [x] mechanic_alias_2

[Paper-Only]: https://papermc.io/downloads/all
[Premium-Only]: Premium-Features