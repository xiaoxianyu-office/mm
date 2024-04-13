If your ModelEngine model vanishes on a server restart, or when you leave the area the mob is in, you need to make sure the Model is applied when the mob loads, not just when it spawns.

Your current mob file may have a line like the following:
```yaml
Skills:
- model{m=Duck;n=name} @self ~onSpawn
```

You can solve the issue by copying your Model mechanic, and changing onSpawn to onLoad. You must keep both in the file, the outcome is the following:
```yaml
Skills:
- model{m=Duck;n=name} @self ~onSpawn
- model{m=Duck;n=name} @self ~onLoad
```