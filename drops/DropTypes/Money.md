## Description
When dropped, gives currency from the `Vault` plugin to the trigger, if a player.  
A `<drop.amount>` [placeholder](/Skills/Placeholders#misc-placeholders) can be used inside the reward message to fetch the amount of money being given. This message can be configured inside the `config-general.yml` file


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| sendmessage | sm      | Whether the preconfigured message should be sent to the player       | true    |


## Examples
```yaml
  Drops:
  - money 20
```


## Aliases
- [x] vault
- [x] currency