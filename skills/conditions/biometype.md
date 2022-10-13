**Description:** Tests if the target is within the given list of biome types

---

**Attributes:**

| Attribute | Alias | Description                       |
|-----------|-------|-----------------------------------|
| type      | t     | A list of biomes to check         |
| exact     | e     | Whether to match the type exactly |

---

**Examples:**

```
Conditions:
- biometype{t=jungle,ocean,extreme_hills} true
```
---

**Biome Types**
- none
- taiga
- extreme_hills
- jungle
- mesa
- plains
- savanna
- icy
- the_end
- beach
- forest
- ocean
- desert
- river
- swamp
- mushroom
- nether
- underground
- mountain

---

**Extra Information:**

- [x] Type: Location
- [x] Aliases: biomecategory