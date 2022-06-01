**Description:** This condition tests if the target is within the given list of biomes.

---

**Attributes:**

| Attribute | Alias | Description              |
| --------- | ----- | ------------------------ |
| biome     | b     | A list of biomes to check|

---

**Examples:**

```
Conditions:
- biome DESERT,DESERT_HILLS
```

If using a custom biome (like from a datapack), you can define it with the namespaced key like this:

```
Conditions:
- biome far_end:void,far_end:warped_marsh
```

---

**Extra Information:**

- [x] Type: Location