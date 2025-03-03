## Description
Checks for the current lunar phase


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| phases    | p, phase  | the lunar phase/s you want to check for. Can be a list.              | 0<!--type:0,1,2,3,4,5,6,7--><!--list-->|

### Phase Attribute
Please note that you **MUST** use the phase number. This chart is here to help you match the lunar phase to its number.

|   Phase Name    | Phase Number |
| --------------- | -------------|
| Full Moon       |       0      |
| Waning Gibbous  |       1      |
| Third Quarter   |       2      |
| Waning Crescent |       3      |
| New Moon        |       4      |
| Waxing Crescent |       5      |
| First Quarter   |       6      |
| Waxing Gibbous  |       7      |


## Examples
```yaml
  Conditions:
  - lunarphase{p=0} true
```
```yaml
  Conditions:
  - lunarphase{p=0,2,4,6} true
```