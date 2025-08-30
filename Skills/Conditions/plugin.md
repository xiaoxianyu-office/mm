## Description
Checks if the specified plugin is running on the server


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| plugin    | pl, p     | The plugin to check for                                           | MythicMobs |


## Examples
```yml
  Conditions:
  - plugin{p=ThePluginName} true
```


## Aliases
- [x] pluginexists
- [x] hasplugin