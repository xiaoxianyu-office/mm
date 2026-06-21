## Description
Applies an [aura] component to the target entity that keeps the chunk(s) containing the aura holder force-loaded for the duration of the aura

> [!tip]
> This prevents the holder from unloading (and thus freezing) when no player is nearby, which is useful for bosses that must remain active after their combatant dies

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius | r | chunk radius to keep loaded around the holder (0 = own chunk only, capped at the server's simulation distance | 0 |
| lag | tps, tpsthreshold | if the server's 1-minute TPS average drops at or below this value the aura terminates, releasing the force-load | 0 |


## Aliases
- [x] keeploaded
- [x] loadchunk