## Introduction
The value of certain attributes can be not only a static value, but also a value containing placeholders.  
> While this piece of information is not contained in the documentation, you can check it by using the [MythicScribe](https://marketplace.visualstudio.com/items?itemName=Lxlp.mythicscribe) extension and hovering over an attribute or a mechanic

Those attributes that can have placeholders in their values are always parsed when the associated mechanic is executed, so that their value can always better reflect the current state of the mob, the target, the [SkillTree](/Skills/SkillTrees) and the likes

## Mythic Placeholder Recognition

A Mythic placeholder has the generic syntax of `<placeholder.segment1{attribute=value;attribute2=value2}.segment2.segment3{}>`

In a text, as soon as a `<` character is spotted If

- The found `<` would start a new placeholder
- The character following `<` is **NOT**
  - another `<`
  - a space ` `
  - an equal sign `=`


from that point forward and as long as a matching number of `>` has not been found, that portion of text will be evaluated as a (possible!) Mythic placeholder. If no matching Mythic placeholder is found, the literal value of the placeholder is returned

### Examples
- `<skill.var.example>`: Will return the value of the variable
- `<red>`: <red> is not a Mythic placeholder, so a `<red>`string will be returned
- `<<skill.var.amount>`: The first `<` is followed by another `<`, which is a "blacklisted" character, so the first `<` will be treated as a simple string. On the other hand, the second `<` is a valid character to be starting a placeholder, so `<skill.var.amount>` gets correctly recognized as a placeholder. As a result, if we say that the value of the skill scoped variable is `N`, the result of this parsing will be `<N`

## Parsing Order

When a Placeholder is parsed, the operation *always* has certain steps that are executed in order
- Mythic placeholders are replaced with their value
- Papi placeholders are replaced with their value
  - If the targeted entity is a player, the Papi placeholders will be parsed against said player
- Math operations are parsed.
  - At this exact step, functions and operators in the [Math's](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Skills/Math) wiki page are also interpreted and used
  - This happens only if the attribute's specific placeholder type (PlaceholderInteger, PlaceholderFloat etc.) has support for such, and some specific character (`*`, `-`, `+` etc.) appears in the string
    - A PlaceholderString placeholder will not parse math
    - A PlaceholderInt placeholder will parse math

## Compound parsing

Please **take note** of the fact that each step in this process happens against whatever was already parsed in previous steps. So, for instance, you can have something like this
```yaml
  - setvariable{var=skill.somevar;val=1}
  - setvariable{var=skill.example;type=STRING;val=%some_papi_placeholder_<skill.var.somevar>%}
```

Where, in order
- `<skill.var.somevar>` will be replaced with its value, which is the literal `1`
- The papi placeholder `%some_papi_placeholder_{string}%` will be parsed NOT against the literal string `<skill.var.somevar>`, but the already parsed value, which is `1`

So that the value stored in `<skill.var.somevar>` can be used inside of the papi placeholder.  

> At the same time, please do take abundant note that, given the parsing order, while it is possible to make a papi placeholder returns some mythic-parseable placeholder (for instance, by making `%some_other_papi_placeholder%` return stuff like `<skill.var.test>`), those will NOT be parsed, since their "turn" has already passed  

If we were to apply this to math operations too, we could also obtain something like the following
```yaml
  - setvariable{var=skill.example;val=(1<skill.var.operation>3) + 4}
```
where the value of `<skill.var.operation>` will be inserted in the middle of 1 and 2. So
- If `<skill.var.operation>` is +, the value will be the result of the (1+3)+4 math operation
- If `<skill.var.operation>` is -, the value will be the result of the (1-3)+4 math operation
- If `<skill.var.operation>` is 2, the value will be the result of the (123)+4 math operation
- if `<skill.var.operation>` is -2, the value will be the result of the (1-23)+4 math operation