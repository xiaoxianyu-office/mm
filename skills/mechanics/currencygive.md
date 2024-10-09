## Description
Gives money to players.  
This mechanic needs the Vault plugin and an economy plugin installed to
work and Vault must be enabled in the MythicMobs `config-general.yml` file
```yaml
    Vault:
      Enabled: true
```

## Attributes
| Attribute | Aliases | Description          | Default |
|-----------|---------|----------------------|---------|
| amount    | a       | The amount of money. | 0.0     |

  

## Examples
```yaml
  Skills:
  - currencygive{amount=20} @pir{r=20} ~onSpawn 0.2
```
If executed all players in radius of 20 blocks around the spawned mob
will receive 20 money by a chance of 20%


## Aliases
- [x] giveCurrency