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
    <version>5.12.1</version>  
    <scope>provided</scope>
</dependency>
```
#### Gradle (Groovy)
```groovy
dependencies {
    //...
    compileOnly 'io.lumine:Mythic-Dist:5.12.1'
}
```
#### Gradle (Kotlin)
```kotlin
dependencies {
    // ...
    compileOnly("io.lumine:Mythic-Dist:5.12.1")
}
```
--------------------------

# Placeholders
You can find the Placeholders API [here](/API/Placeholders)

---

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

Registering Custom Components
-----------------------------
Addons can register their own mechanics, conditions, targeters, and placeholders using the same annotation-based system Mythic uses internally, plus custom triggers. Add MythicMobs to `depend` (or `softdepend`) in your `plugin.yml` first.

### Custom Mechanics
A mechanic is a class annotated with `@MythicMechanic`, extending `SkillMechanic`, and implementing one of the dispatch interfaces:

- `INoTargetSkill` — `SkillResult cast(SkillMetadata data)`
- `ITargetedEntitySkill` — `SkillResult castAtEntity(SkillMetadata data, AbstractEntity target)`
- `ITargetedLocationSkill` — `SkillResult castAtLocation(SkillMetadata data, AbstractLocation target)`

The constructor must match the superclass signature `(SkillExecutor, File, String, MythicLineConfig)`. Read your attributes from the `MythicLineConfig`.

```java
package com.example.myplugin.mythic.mechanics;

import io.lumine.mythic.api.adapters.AbstractEntity;
import io.lumine.mythic.api.config.MythicLineConfig;
import io.lumine.mythic.api.skills.ITargetedEntitySkill;
import io.lumine.mythic.api.skills.SkillMetadata;
import io.lumine.mythic.api.skills.SkillResult;
import io.lumine.mythic.core.skills.SkillExecutor;
import io.lumine.mythic.core.skills.SkillMechanic;
import io.lumine.mythic.core.utils.annotations.MythicMechanic;
import org.bukkit.entity.Player;

import java.io.File;

@MythicMechanic(author = "You", name = "greet", aliases = {"hello"},
        description = "Sends a message to the target player")
public class GreetMechanic extends SkillMechanic implements ITargetedEntitySkill {

    private final String message;

    public GreetMechanic(SkillExecutor manager, File file, String line, MythicLineConfig mlc) {
        super(manager, file, line, mlc);
        this.message = mlc.getString(new String[]{"message", "msg", "m"}, "Hello!");
    }

    @Override
    public SkillResult castAtEntity(SkillMetadata data, AbstractEntity target) {
        if (target.isPlayer()) {
            ((Player) target.getBukkitEntity()).sendMessage(message);
        }
        return SkillResult.SUCCESS;
    }
}
```

Used in config as `- greet{message=Hi!} @target`.

### Custom Conditions & Targeters
Conditions and targeters follow the same pattern. Annotate the class and extend the matching base type:

- **Conditions** — `@MythicCondition`, extend `SkillCondition` and implement `IEntityCondition`, `ILocationCondition`, or `ISkillMetaCondition`.
- **Targeters** — `@MythicTargeter`, extend `IEntitySelector` (entity targeters) or `ILocationSelector` (location targeters).

Both are picked up by the same package scan shown below.

### Registering Mechanics, Conditions & Targeters
Create a `CustomComponentRegistry` pointing at the package(s) holding your annotated classes. The constructor automatically scans for mechanics, conditions, targeters, and drops:

```java
// in your plugin's onEnable(), after MythicMobs is enabled
new CustomComponentRegistry(this, "com.example.myplugin.mythic");
```

You can also register a specific component type from a specific package:

```java
new CustomComponentRegistry(this, "com.example.myplugin.mythic")
        .registerCustomComponent(CustomComponentRegistry.MythicComponentType.MECHANIC,
                "com.example.myplugin.mythic.mechanics");
```

### Custom Placeholders
Placeholders use the `@MythicPlaceholder` annotation and are registered with the `PLACEHOLDER` component type. They are **not** picked up by the base package scan, so register them explicitly:

```java
new CustomComponentRegistry(this, "com.example.myplugin.mythic")
        .registerCustomComponent(CustomComponentRegistry.MythicComponentType.PLACEHOLDER,
                "com.example.myplugin.mythic.placeholders");
```

See the full [Placeholders API](/API/Placeholders) page for how to write a placeholder class, fetch arguments, and use the scoped and wildcard variants.

### Custom Triggers
A trigger is a `SkillTrigger` created with a name and optional aliases, then registered:

```java
import io.lumine.mythic.api.skills.SkillTrigger;

public final class MyTriggers {

    public static final SkillTrigger CUSTOM_EVENT =
            SkillTrigger.create("CUSTOMEVENT", "MYEVENT");

    public static void register() {
        SkillTrigger.register(CUSTOM_EVENT);   // or: CUSTOM_EVENT.register();
    }
}
```

Call `MyTriggers.register()` in your `onEnable()`. In mob configs the trigger is referenced by adding the `~on` prefix to the registered name — Mythic strips `~on` and matches the rest case-insensitively. So `CUSTOMEVENT` is used as `~onCustomEvent`, and the alias `MYEVENT` as `~onMyEvent`.

To make a mob's skills with that trigger actually fire, dispatch it through the event bus. The caster is the `SkillCaster` running the skill (an `ActiveMob` is a `SkillCaster`); `triggerEntity` is the entity that caused it, or `null`:

```java
ActiveMob mob = ...;                 // your MythicMob (implements SkillCaster)
AbstractEntity triggerEntity = ...;  // the cause, may be null

MythicBukkit.inst().getSkillManager().getEventBus()
        .processTrigger(MyTriggers.CUSTOM_EVENT, mob, triggerEntity, /* sync */ false);
```

Events
------

The Mythic API exposes the following Bukkit events. Full method signatures and fields are documented in the [JavaDocs](https://www.mythiccraft.io/javadocs/mythic/). A checkmark in the *Cancellable* column means the event implements `Cancellable`.

### Reload & Lifecycle
| Event | Description | Cancellable |
|-------|-------------|:-----------:|
| MythicPreReloadEvent | Fired at the start of the reload command before reload work begins. |  |
| MythicReloadEvent | Fired after Mythic reloads configuration in reload stage one. |  |
| MythicReloadedEvent | Fired after reload stage two completes and clocks are reloaded. |  |
| MythicPostReloadedEvent | Fired after MythicReloadedEvent during reload stage two. |  |
| MythicReloadCompleteEvent | Fired at the end of reload processing after completion messaging. |  |

### Config Loading
| Event | Description | Cancellable |
|-------|-------------|:-----------:|
| MythicConditionLoadEvent | Requests a custom condition implementation for a config entry. |  |
| MythicMechanicLoadEvent | Requests a custom mechanic implementation for a config entry. |  |
| MythicTargeterLoadEvent | Requests a custom targeter implementation for a config entry. |  |
| MythicDropLoadEvent | Requests a custom drop implementation for a config entry. |  |
| MythicPlaceholdersLoadEvent | Event fired as MythicMobs registers placeholders, before it finalizes them |  |
| MythicStatsRegistrationEvent | Fired after Mythic registers its built-in primary stats. |  |
| MythicMenusPreLoadEvent | Fired immediately before Mythic loads custom menu configs. |  |

### Mobs
| Event | Description | Cancellable |
|-------|-------------|:-----------:|
| MythicMobPreSpawnEvent | Fired before Mythic attempts to spawn a mob entity. | yes |
| MythicMobPreSpawnConfigureEvent | Called when a MythicMob is about to be spawned and currently in pre-spawn configuration stage |  |
| MythicMobSpawnEvent | Fired after a Mythic mob entity is created and wrapped, but before registration. | yes |
| MythicMobDeathEvent | Fired for active Mythic mobs during Bukkit death handling. |  |
| MythicMobDespawnEvent | Fired when an active Mythic mob despawns through Mythic's despawn handler. |  |
| MythicMobInteractEvent | Fired when a player right-clicks an active Mythic mob. |  |
| MythicMobEggEvent | Fired when a player uses a Mythic egg item. | yes |
| MythicMobLootDropEvent | Fired when Mythic has generated a loot bag for a mob death context. |  |
| MythicMobItemGenerateEvent | Fired when a Mythic item definition has been materialized into a Bukkit stack. |  |

### Combat & Skills
| Event | Description | Cancellable |
|-------|-------------|:-----------:|
| MythicDamageEvent | Fired when a Mythic damage mechanic prepares to apply damage to a target. | yes |
| MythicHealMechanicEvent | Fired when a Mythic healing mechanic is about to apply healing. | yes |
| MythicSkillEvent | Fired before a Mythic skill executes its mechanic queue. | yes |
| MythicTriggerEvent | Fired before Mythic executes trigger mechanics for a parent skill. |  |
| MythicTargetEvent | Fired after a Mythic targeter is resolved but before the fallback is checked. |  |
| MythicProjectileHitEvent | Fired when a Mythic projectile tracker intersects an entity target. |  |
| MythicPlayerAttackEvent | Represents a player attack context in Mythic's Bukkit event layer. |  |

### Auras, Stats & Items
| Event | Description | Cancellable |
|-------|-------------|:-----------:|
| MythicAuraStartEvent | Called when an Aura is about to be applied to an entity or location Cancelling this event will prevent the aura from being applied | yes |
| MythicAuraStopEvent | Called when an Aura is stopped/terminated |  |
| MythicStatChangeEvent | Fired when a tracked stat value changes for a caster. |  |
| MythicApplyEnchantEvent | Fired before Mythic applies one enchantment to an item. |  |
| MythicModifiedInventoryEvent | Fired after Mythic mutates a Bukkit player's inventory. |  |

### Cinematics
| Event | Description | Cancellable |
|-------|-------------|:-----------:|
| MythicCinematicStartEvent | Fired before a cinematic camera path begins playing for a player. | yes |
| MythicCinematicEndEvent | Fired when a cinematic camera path ends for a player (natural finish, manual cancel, player quit, or player death). |  |

### Players & Variables
| Event | Description | Cancellable |
|-------|-------------|:-----------:|
| MythicPlayerLoadedEvent | Fired after a PlayerData profile is initialized for an online player. |  |
| MythicPlayerQuitEvent | Fired when Mythic unloads a player's profile during quit handling. |  |
| MythicPlayerSignalEvent | Fired when the signal mechanic targets a player profile. |  |
| MythicPlayerVariableSetEvent | Fired before a player variable entry is written. |  |
| MythicPlayerVariableRemoveEvent | Describes removal of a player variable entry. |  |

### Packets (advanced)
| Event | Description | Cancellable |
|-------|-------------|:-----------:|
| MythicPacketItemDataEvent | Fired for outbound item stack packets intercepted by volatile packet handlers. |  |
| PlayerActionPacketEvent | Fired for inbound player action packets intercepted by volatile packet handlers. | yes |
