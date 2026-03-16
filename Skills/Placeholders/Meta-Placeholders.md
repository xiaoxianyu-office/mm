You can append some keywords (that we will call `meta keywords`), each specific to a placeholder's type, at the end of a placeholder in order to modify its return value and type.

```yaml
<some.placeholder.{keywords}>
```

Each keyword has an
- `Input Type`, which is the placeholder type the keyword applies to
- `Output Type`, which is the placeholder type that can be created from the keyword's returned value

> Placeholder support is allowed in every place inside of meta keywords, so each keyword can also be another placeholder to be parsed

---

```yaml
<caster.name.capitalize>
```
> `<caster.name>` returns a STRING<br>
> Among all keywords for the String type, we are using the `capitalize` one, which has as an output a String type. This means that
> - It is applied to a String value
> - It does some form of conversion to its value (in this case, capitalizing every character of the string)
> - It returns a String value


```yaml
<caster.name.size>
```
> `<caster.name>` returns a STRING<br>
> Among all keywords for the String type, we are using the `size` one, which has as an output an Integer type. This means that
> - It is applied to a String value
> - It does some form of conversion to its value (in this case, returning the length of the string)
> - It returns an Integer value

---

Given that each meta keyword has a specific input and output type, it is possible to *chain* them together, obtaining a compound effect where each keyword coverts the previous value and pass the result to the following one

```yaml
<skill.var.exampleString.substring{from=0;to=9}.size.add{amount=1}>
```
> Among all keywords for the String type, we are using the `substring` one, which has as an output a String type. This means that
> - It is applied to a String value
> - It does some form of conversion to its value (in this case, extracting the first 10 characters from the string)
> - It returns a String value
>
> Among all keywords for the String type, we are using the `size` one, which has as an output an Integer type. This means that
> - It is applied to a String value (which the `substring` keyword just returned)
> - It does some form of conversion to its value (In this case, returning the length of the string, which we know will be between 0 and 10)
> - It returns an Integer value
>
> Among all keywords for the Integer type, we are using the `add` one, which has as an output an Integer type. This means that
> - It is applied to an Integer value (which the `size` keyword just returned)
> - It does some form of conversion to its value (In this case, adding a value of 1 to the integer's value)
> - It returns an Integer value

[[_TOC_]]

# Universal Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .cache       |             | Given the input value and the keywords used after it, this keyword will cache the result the first time the placeholder is parsed, and directly return the cached value each subsequent parsing |
| .formatted   | STRING      | Returns a more human-readable version of the input value |
|. typename    | STRING      | Returns the type name of the previous value's return type | 
| .toInteger | INTEGER | Converts the value to an Integer without doing any specific operation, allowing chaining for Integer meta keywords |
| .toFloat | FLOAT | Converts the value to a Float without doing any specific operation, allowing chaining for Float meta keywords |
| .toLong | LONG | Converts the value to a Long without doing any specific operation, allowing chaining for Long meta keywords |
| .toDouble | DOUBLE | Converts the value to a Double without doing any specific operation, allowing chaining for Double meta keywords |
| .toBoolean | BOOLEAN | Converts the value to a Boolean without doing any specific operation, allowing chaining for Boolean meta keywords |
| .toString | STRING | Converts the value to a String without doing any specific operation, allowing chaining for String meta keywords |
| .toLocation | LOCATION | Converts the value to a Location without doing any specific operation, allowing chaining for Location meta keywords |
| .toVector | VECTOR | Converts the value to a Vector without doing any specific operation, allowing chaining for Vector meta keywords |
| .toList | LIST | Converts the value to a List without doing any specific operation, allowing chaining for List meta keywords |
| .toSet | SET | Converts the value to a Set without doing any specific operation, allowing chaining for Set meta keywords |
| .toMap | MAP | Converts the value to a Map without doing any specific operation, allowing chaining for Map meta keywords |
| .toTime | TIME | Converts the value to a Time without doing any specific operation, allowing chaining for Time meta keywords |
> [Go To Explanation>>](#)  

# Integer Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .add{amount=[Integer]} | INTEGER | The addition between the value and the specified Integer |
| .sub{amount=[Integer]} | INTEGER | The subtraction between the value and the specified Integer |
| .mul{amount=[Integer]} | INTEGER | The multiplication between the value and the specified Integer |
| .div{amount=[Integer]} | INTEGER | The division between the value and the specified Integer |
| .abs | INTEGER | The absolute value of the value |
> [Go To Explanation>>](#)  

# Float Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .add{amount=[Float]} | FLOAT | The addition between the value and the specified Float |
| .sub{amount=[Float]} | FLOAT | The subtraction between the value and the specified Float |
| .mul{amount=[Float]} | FLOAT | The multiplication between the value and the specified Float |
| .div{amount=[Float]} | FLOAT | The division between the value and the specified Float |
| .abs | FLOAT | The absolute value of the value |
| .round | INTEGER | Rounds the value to the nearest Integer |
| .precision{amount=[Integer]} | FLOAT | Returns the same float value, but with a given maximum precision. Extra precision is rounded using the HALF_UP rounding mode |
> [Go To Explanation>>](#)  

# Long Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .add{amount=[Long]} | LONG | The addition between the value and the specified Long |
| .sub{amount=[Long]} | LONG | The subtraction between the value and the specified Long |
| .mul{amount=[Long]} | LONG | The multiplication between the value and the specified Long |
| .div{amount=[Long]} | LONG | The division between the value and the specified Long |
| .abs | LONG | The absolute value of the value |
> [Go To Explanation>>](#)  

# Double Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .add{amount=[Double]} | DOUBLE | The addition between the value and the specified Double |
| .sub{amount=[Double]} | DOUBLE | The subtraction between the value and the specified Double |
| .mul{amount=[Double]} | DOUBLE | The multiplication between the value and the specified Double |
| .div{amount=[Double]} | DOUBLE | The division between the value and the specified Double |
| .abs | DOUBLE | The absolute value of the value |
| .round | LONG | Rounds the value to the nearest Long |
| .precision{amount=[Integer]} | DOUBLE | Returns the same float value, but with a given maximum precision. Extra precision is rounded using the HALF_UP rounding mode |
> [Go To Explanation>>](#)  

# Boolean Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .inverse     | BOOLEAN     | The inverse of the value |
| .number      | INTEGER     | The value as either a 0 (false) or 1 (true) |
| .yesno       | STRING      | The value as either a no (false) or yes (true) |
| .union.{Boolean} | BOOLEAN | Logical OR with specified Boolean |
| .intersection.{Boolean} | BOOLEAN | Logical AND with specified Boolean |
| .difference.{Boolean} | BOOLEAN | True if value is true and argument is false |
> [Go To Explanation>>](#)  

# String Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .size | INTEGER | The length of the string |
| .uppercase | STRING | The string in uppercase |
| .lowercase | STRING | The string in lowercase |
| .capitalize | STRING | The string with the first character in uppercase |
| .trim | STRING | The string with leading and trailing spaces removed |
| .replace{from=old;to=new} | STRING | The string with occurrences of `old` replaced by `new` |
| .remove{value=text} | STRING | The string with occurrences of `text` removed |
| .contains{value=text} | BOOLEAN | Whether the string contains `text` |
| .substring{from=[Integer];to=[Integer]} | STRING | A substring from the `from` index to the `to` index |
| .shift{amount=[Integer]} | STRING | Removes the first `Integer` characters |
| .split{regex=[String];with=[String]} | STRING | Splits the string by `regex`, then joins it with the `with` string |
| .indexof{value=[String]} | INTEGER | The index of the first occurrence of the `value` text |
| .lastindexof{value=[String]} | INTEGER | The index of the last occurrence of the `value` text |
| .startswith{value=[String]} | BOOLEAN | Whether the string starts with `value` |
| .endswith{value=[String]} | BOOLEAN | Whether the string ends with `value` |
| .append{value=[String]} | STRING | Appends `value` to the end of the string |
| .prepend{value=[String]} | STRING | Prepends `value` to the beginning of the string |
| .insert{index=[Integer];value=[String]} | STRING | Inserts `value` at the specified `index` |
| .regex{regex=[String]} | BOOLEAN | Whether the string matches the `regex` pattern |
| .{index} | STRING | Returns the character at the specified `index` |
> [Go To Explanation>>](#)  

# Set Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .size | INTEGER | The number of elements in the set |
| .join{with=[String]} | STRING | Joins all elements using the `with` delimiter |
| .contains{value=[String]} | BOOLEAN | Whether the set contains the given `value` |
> [Go To Explanation>>](#)  

# Location Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .x | DOUBLE | The X coordinate |
| .y | DOUBLE | The Y coordinate |
| .z | DOUBLE | The Z coordinate |
| .world | STRING | The world name |
| .yaw | DOUBLE | The yaw |
| .pitch | DOUBLE | The pitch |
| .coords | LIST | A list with the X, Y, and Z coordinates. Also useful if you want to call .toVector on it |
> [Go To Explanation>>](#)  

# Vector Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .x | DOUBLE | The X component |
| .y | DOUBLE | The Y component |
| .z | DOUBLE | The Z component |
| .normalized | VECTOR | The normalized vector |
| .length | DOUBLE | The length (magnitude) of the vector |
| .add{amount=[Vector]} | VECTOR | Adds another vector |
| .sub{amount=[Vector]} | VECTOR | Subtracts another vector |
| .mul{amount=[Vector]} | VECTOR | Multiplies the vector by another vector |
| .div{amount=[Vector]} | VECTOR | Divides the vector by another vector |
| .rotate{axis=[String];angle=[Double]} | VECTOR | Rotates the vector around `axis` by `angle` radians |
> [Go To Explanation>>](#)  

# List Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .size | INTEGER | Number of elements in the list |
| .first | STRING | First element in the list |
| .last | STRING | Last element in the list |
| .reverse | LIST | The list reversed |
| .sort | LIST | The list sorted alphabetically |
| .sortnum | LIST | This list sorted numerically. Each element of the list needs to be a number |
| .shuffle | LIST | Shuffles the list, randomizing its elements |
| .get{index=[Integer]} | STRING | Element at specified `index` |
| .join{with=[String]} | STRING | Joins elements using the `with` delimiter |
| .contains{value=[String]} | BOOLEAN | Whether the list contains `value` |
| .maxnumber | DOUBLE | Maximum numerical value in list |
| .minnumber | DOUBLE | Minimum numerical value in list |
| .indexof{value=[String]} | INTEGER | Index of first occurrence of `value` |
| .lastindexof{value=[String]} | INTEGER | Index of last occurrence of `value` |
| .slice{from=[Integer];to=[Integer]} | LIST | Slice of list from `from` to `to` |
| .slicefrom{from=[Integer]} | LIST | Slice of list from `from` to end |
| .sliceto{to=[Integer]} | LIST | Slice of list from start to `to` |
| .append{value=[String]} | LIST | Adds `value` to the end of the list |
| .prepend{value=[String]} | LIST | Adds `value` to the start of the list |
| .insert{index=[Integer];value=[String]} | LIST | Inserts `value` at the given `index` |
| .remove{index=[Integer]} | LIST | Removes value at given `index` |
| .{index} | STRING | Element at specified `index` |
> [Go To Explanation>>](#)  

# Map Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .size | INTEGER | Number of key-value pairs |
| .keys | LIST | List of all keys |
| .values | LIST | List of all values |
| .get{key=[String]} | STRING | Value associated with the specified `key` |
| .{key} | STRING | Value associated with the specified `key` |
> [Go To Explanation>>](#)  

# Time Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .delta{value=[Long]} | INTEGER | Difference between the value's time and the and given `value` timestamp |
| .formatted{value=[String]} | STRING | Formatted date/time using the specified pattern. The pattern can be anything the Java function [ZoneOffset.of](https://docs.oracle.com/javase/8/docs/api/java/time/ZoneOffset.html#of-java.lang.String-) accepts |
| .duration | STRING | Interprets the Time as a raw "amount of milliseconds" and displays the total amount of Seconds, Minutes, Hours, Days, Months and Years. Can be useful for countdowns and the likes, especially if paired with the `.delta` meta keywords|
> [Go To Explanation>>](#)  

# Item Meta Keywords  
| Placeholder | Return Type | Return Value |
|-------------|-------------|--------------|
| .withType{type=[String]} | ITEM | Returns the same item but with its type set to the specified `type` material (case-insensitive, must match a valid `Material` enum) |
| .withDurability{durability=[Integer]} | ITEM | Returns the same item but with its durability set to the specified integer `durability` |
| .withMaxDurability{durability=[Integer]} | ITEM | Returns the same item but with its maximum durability set to the specified integer `durability` |
| .withLore{lore=[List]} | ITEM | Returns the same item but with its lore set to the specified list of strings. |
| .withName{name=[String]} | ITEM | Returns the same item but with its display name set to `name` |
| .withMythicType{type=[String]} | ITEM | Returns the same item but with its persistent "Mythic Type" set to `type`, allowing you to make Mythic believe the modified item is the `type` mythic item |
| .withEnchants{enchant=[Map]} | ITEM | Returns the same item but with enchantments replaced by those provided in the map. Removes all previous enchantments before applying the new ones |
| .withCustomData{namespace=[String];key=[String];value=[String]} | ITEM | Returns the same item but with custom persistent data (`value` stored under `namespace:key`) |
| .withAmount{amount=[Integer]} | ITEM | Returns the same item but with its stack amount set to `value` |
| .withUUID{uuid=[String]} | ITEM | Returns the same item but with its UUID nbt set to the specified value |
| .withTimestamp{timestamp=[Long]} | ITEM | Returns the same item but with its timestamp nbt set to the specified integer value |
| .withCustomModelData{value=[String]} | ITEM | Returns the same item but with its Custom Model Data set to `value` |
| .withModel{namespace=[String];value=[String]} | ITEM | Returns the same item but with its item model set to `{namespace}:{path}` |
| .type | STRING | The item's type as a string (Material name) |
| .durability | INTEGER | The current durability value of the item |
| .maxDurability | INTEGER | The maximum durability value of the item |
| .lore | LIST | The item's lore as a list of strings |
| .name | STRING | The display name of the item |
| .mythicType | STRING | The persistent "Mythic Type" value of the item, if set |
| .enchants | MAP | A map of all enchantments on the item |
| .getCustomData{namespace=[String];key=[String]} | STRING | The string value stored in the item's custom persistent data under `{namespace}:{key}` |
| .customModelData | INTEGER | The item's Custom Model Data value |
| .model | STRING | The item's model identifier in `namespace:path` format |
| .amount | INTEGER | The stack amount of the item |
> [Go To Explanation>>](#)  
