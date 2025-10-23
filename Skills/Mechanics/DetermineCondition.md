## Description
Determines the outcome of a Metaskill that is used as a Condition via the [MetaskillCondition](/Skills/Conditions/MetaskillCondition) condition


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| determination | det | Modifies whether the associated condition should return or not. Can be `true` or `false` | true |
| mode |  | How the determination value is modified. Can be `SET`, `OR`, `AND`, `NOT`. Works like you would expect a [boolean operation](https://en.wikipedia.org/wiki/Boolean_algebra#Boolean_operations) to, apart from SET that simply overrides any already defined determination value | SET<!--type:SET,AND,NOT,OR-->|


## Examples
```yaml
  Skills:
  - determinecondition{determination=true} @self
```


## Aliases
- [x] detCond