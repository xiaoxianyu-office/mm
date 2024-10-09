## Description
Takes money from players.  
This mechanic needs the Vault plugin and an economy plugin installed to
work.  
It also requires Vault being enabled in the [config.yml](/configuration/)
```yaml
        Vault:
          Enabled: true
```

## Attributes
| Attribute | Aliases | Description                            | Default |
|-----------|---------|----------------------------------------|---------|
| amount    | a       | The amount of money taken from player. | 0.0     |

  

## Examples
This skill will take away 20 money from all players in radius of 20 blocks.
```yaml
  Skills:
  - currencytake{amount=20} @pir{r=20} ~onSpawn
```


## Aliases
- [x] takeCurrency