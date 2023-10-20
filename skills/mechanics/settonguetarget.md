==============

## Description:

Sets the tongue target for a frog caster to the target entity.

## Attributes:

| Attribute | Alias | Description |
| --------- | ----- | ----------- |
| none      | none  | none        |

## Examples:

Sets the frog's tongue to the trigger trigger when right clicked.
```yaml
MyLovingFrog:
  Type: FROG
  Skills:
    - setTongueTarget @trigger ~onInteract
```