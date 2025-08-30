## Description
Matches the last signal received by the target mob


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| signal    | s         | The signal to match                                                  | DEFAULT |


## Examples
```yaml
  Conditions:
  - lastsignal{s=fireCannonShot} true
```