**Description:** 

Changes the skybox of the target.

---

**Attributes:**

| Attribute        | Alias | Description                                                   |
| ---------------- | ----- | ------------------------------------------------------------- |
| skybox           | sky, s, type, t, environment, env, e | What skybox should be shown to the player | 

**Availd value for Skybox:**

| Value | Description |
| ----- | ----------- |
| Any Integer Below 1 | Cancel the modified skybox |
| Any Integer Above 0 | Rainy |
---

**Examples:**

Makes the target see the end skybox

```
- skybox{s=1} @PIR{r=20}
```