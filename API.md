JavaDocs
--------

JavaDocs for Mythic API can be found here:

1.  <https://www.mythiccraft.io/javadocs/mythic/>

-------------------------
## Repositories

#### Maven
```xml
<repository>
    <id>nexus</id>
    <name>Lumine Releases</name>
    <url>https://mvn.lumine.io/repository/maven-public/</url>
</repository>
```
#### Gradle (Groovy)
```groovy
repositories {
    // ...
    mavenCentral()
    maven { url 'https://mvn.lumine.io/repository/maven-public/' }
}
```
#### Gradle (Kotlin)
```kotlin
repositories {
    // ...
    mavenCentral()
    maven(url = "https://mvn.lumine.io/repository/maven-public/")
}
```

## Dependencies
#### Maven
```xml
<dependency>
    <groupId>io.lumine</groupId>
    <artifactId>Mythic-Dist</artifactId>
    <version>5.6.1</version>  
    <scope>provided</scope>
</dependency>
```
#### Gradle (Groovy)
```groovy
dependencies {
    //...
    compileOnly 'io.lumine:Mythic-Dist:5.6.1'
}
```
#### Gradle (Kotlin)
```kotlin
dependencies {
    // ...
    compileOnly("io.lumine:Mythic-Dist:5.6.1")
}
```
--------------------------

Examples
--------
The MythicMobs API contains numerous events and helper classes to help
you utilize our mobs, items, and skill systems.

Some examples to help you get started can be found here:

1.  [MythicMobs API Examples Repo](https://github.com/xikage/MythicMobs-API-Examples)

### Spawning a MythicMob

```java
MythicMob mob = MythicBukkit.inst().getMobManager().getMythicMob("SkeletalKnight").orElse(null);
Location spawnLocation = player.getLocation();
if(mob != null){
    // spawns mob            
    ActiveMob knight = mob.spawn(BukkitAdapter.adapt(spawnLocation),1);
    
    // get mob as bukkit entity
    Entity entity = knight.getEntity().getBukkitEntity();
}
```

### Check if a Bukkit Entity is a MythicMob
```java
Entity bukkitEntity = ...;
boolean isMythicMob = MythicBukkit.inst().getMobManager().isMythicMob(bukkitEntity);
if(isMythicMob){
    // ...             
}
```

### Get ActiveMob instance from Bukkit Entity
```java
Entity bukkitEntity = ...;
Optional<ActiveMob> optActiveMob = MythicBukkit.inst().getMobManager().getActiveMob(bukkitEntity.getUniqueId());
optActiveMob.ifPresent(activeMob -> {
    //...
}).orElse(() -> /* ... */);
```

### Get a collection of ActiveMobs using a predicate
```java
Collection<ActiveMob> activeMobs = MythicBukkit.inst().getMobManager().getActiveMobs(am -> am.getMobType().equals("SkeletalKnight"));
```
<!--
Events
------

|                                                                  |                                                |
|------------------------------------------------------------------|------------------------------------------------|
| Event                                                            | Description                                    |
| [MythicReloadedEvent](/api/events/MythicReloadedEvent)           | Called when the plugin is reloaded             |
| [MythicMobSpawnEvent](/api/events/MythicMobSpawnEvent)           | Called when a MythicMob spawns                 |
| [MythicMobDeathEvent](/api/events/MythicMobDeathEvent)           | Called when a MythicMob dies                   |
| [MythicMobDespawnEvent](/api/events/MythicMobDespawnEvent)       | Called when a MythicMob despawns without dying |
| [MythicMobLootDropEvent](/api/events/MythicMobLootDropEvent)     | Called right before a loot table is generated  |
| [MythicConditionLoadEvent](/api/events/MythicConditionLoadEvent) | Called when a custom condition is loaded       |
| [MythicDropLoadEvent](/api/events/MythicDropLoadEvent)           | Called when a custom drop is loaded            |
| [MythicMechanicLoadEvent](/api/events/MythicMechanicLoadEvent)   | Called when a custom mechanic is loaded        |
| [MythicTargeterLoadEvent](/api/events/MythicTargeterLoadEvent)   | Called when a custom targeter is loaded        |
-->