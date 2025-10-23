## Description
Sends a resource pack to the targeted player.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| url       | u, link   | The link to the resourcepack to download                             | NONE    |
| hash      | h         | The hash for the resource pack                                    | mythicmobs |


## Examples
> The hash provided in this example is just a demonstration, do not
use it in your skill
```yaml
Skills:
  - sendresourcepack{url="https://yourresourcepackurlhere";hash="cf23df2207d99a74fbe169e3eba035e633b65d94"} @PIR{r=15} ~onSpawn
  - ...
```


## Aliases
- [x] resourcepack