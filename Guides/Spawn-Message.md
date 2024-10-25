**Difficulty: Beginner**

You may have a special mob that spawns, such as a boss, that you want players on the server to know about. You can use the [Message Mechanic](/skills/mechanics/message) combined with the [onSpawn Trigger](/Skills/Triggers/onSpawn) to achieve this.

It is worth noting that this may not work for mobs spawned from a Spawner that is in currently unloaded chunks.

In this basic example, we are simply sending a message to [@server](/Skills/Targeters/PlayersOnServer) informing them that the mob has spawned.

```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  Display: '&6Skeleton King'
  Health: 500
  Damage: 10
  Skills:
  - message{m="&6The Skeleton King has spawned!"} @server ~onSpawn
```

This works well, but you may want to make your mob show its coordinates to players! You can use [Caster Placeholders](/Skills/Placeholders) to achieve this.

```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  Display: '&6Skeleton King'
  Health: 500
  Damage: 10
  Skills:
  - message{m="&6The Skeleton King has spawned! You can find it at, &aX<&co>&b<caster.l.x> &aY<&co>&b<caster.l.y> &aZ<&co>&b<caster.l.x>"} @server ~onSpawn
```

We are using the following placeholders:
- `<&co>` This will insert a `:` symbol which will otherwise interfere with the syntax.
- `<caster.l.x>` This displays the casters X coordinate
- `<caster.l.y>` This displays the casters Y coordinate
- `<caster.l.z>` This displays the casters Z coordinate