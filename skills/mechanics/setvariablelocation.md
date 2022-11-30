Mechanic: Set Variable Location
--------------------------
Sets a value of type string. The value will depend on the location passed to the "value" parameter, and will include informations regarding coordinates and world of the target location

**Attributes**

| Attribute | Alias | Description | Defaults |
| --------- | ----- | ----------- | -------- |
| value      | val, v  | The target location | @self

Examples
--------
```yaml
TestSkill:
 Skills:
 - setvarloc{var=caster.1;v=@self} @self
 - m{m=<caster.var.1>} @self
```