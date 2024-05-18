If your ModelEngine model vanishes on a server restart, or when you leave the area the mob is in, you need to make sure the Model has the `save` attribute set to true  

Your current mob file may have a line like the following:
```yaml
Skills:
- model{m=Duck;n=name} @self ~onSpawn
```

While you can solve the issue by adding the following: 
```yaml
Skills:
- model{m=Duck;n=name;save=true} @self ~onSpawn
```