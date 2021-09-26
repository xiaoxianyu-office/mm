**Description:** 

Kicks the target's screen to simulate recoil.

---

**Attributes:**

| Attribute        | Alias | Description                                                   | Default Values |
| ---------------- | ----- | ------------------------------------------------------------- | -------------- |
| recoil           | r     | The amount of recoil.                                         | 1              |
| pitch            | p     | The range of pitch the screen will get kicked to.             | 1to-1              |
---

Negative numbers on pitch will recoil upwards, whilst positive will recoil downwards. If you set the values to the same number it will always go the same distance: `pitch=-1to-1`

**Examples:**

```
- recoil{r=1;pitch=-1to-1} @self ~onAttack
- recoil{r=4;pitch=10to-10} @self ~onAttack
```