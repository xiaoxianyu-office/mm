Audience attributes can be used to display an effect only to a specific group of players, rather than the entire server, by using the `audience=<audience type>` attribute in a mechanic that supports audiences and specifying an audience type to use. This can be useful in preventing too many particles from being displayed to everyone unnecessarily, and can reduce client-side lag to some extent.

The audience types are:
- `self`/`caster`: the caster of the mechanic
- `nonSelfWorld`/`nonSelf`: every player in the world other than the caster of the mechanic
- `target`: the target of the mechanic
- `world`: every player in the world
- `tracked`/`trackedplayers`/: every player whose client can render the caster
- `nearby`/`nearbyplayers`: every nearby player (closer than `65536` blocks)
- `@Targeter`: every player that the targeter targets

> The default value is `tracked`

Of particular relevance is the `audience=@Targeter` attribute, that allows any entity targeter to be used as the audience of the effect
```yaml
    Skills:
    - effect:particles{particle=reddust;y=2;audience=@Owner} @self
```