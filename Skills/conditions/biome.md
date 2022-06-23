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
- biome{b=DESERT,DESERT_HILLS} true
```

If using a custom biome (like from a datapack), you can define it with the namespaced key like this:

```
Conditions:
- biome{b=far_end:void,far_end:warped_marsh} true
```

---

**Extra Information:**

- [x] Type: Location