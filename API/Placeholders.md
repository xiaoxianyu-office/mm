
[[_TOC_]]

# Creating a new Placeholder
## Step 1 - Create your Placeholder Class inside of a specific package

```java
package your.plugin.compat.mythicmobs.skills.placeholders.all;

public class ExamplePlaceholder {

}
```

> [!tip] About the package
> The package should only contain placeholders you want to register, so it's easier later on to register them in batch

---

## Step 2 - Extend `GenericPlaceholder<T>`
```java
package your.plugin.compat.mythicmobs.skills.placeholders.all;

import io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholder;

public class ExamplePlaceholder extends GenericPlaceholder<String> {

}
```

> [!note] `T` type
> `T` should be the type that is returned by the placeholder. Is your placeholder returning
- a string? use `extends GenericPlaceholder<String>`.
- a location? Use `extends GenericPlaceholder<AbstractLocation>`. 
- an integer? Use `extends GenericPlaceholder<Integer>`.
- ...

> [!caution] Different extend targets
> Other than `GenericPlaceholder<T>`, you can, of course, also extend inheritors of it. MythicMobs already provides a couple more inheriting classes for you to extend from, which will be explained later

---

## Step 3 - Create a Constructor matching the Superclass 
```java
package your.plugin.compat.mythicmobs.skills.placeholders.all;

import io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholder;

public class ExamplePlaceholder extends GenericPlaceholder<String> {
    
    public ExamplePlaceholder(GenericPlaceholderArguments metaContext) {
        super(metaContext);
    }

}
```

> [!important]
> It's imperative that the constructor matches the superclass, otherwise the placeholder will not be able to be registered!

---

## Step 4 - Implement abstract methods

There will (normally) be a couple of different methods to implement:
- some `apply...` method, that will be in charge of parsing the placeholder
- a `convertType` method, to convert the T object to a String
- a `getParsedValueClass` method, to return the Class<T> object of the used T type

> [!tip]
> MythicMobs already comes bundled with some interfaces that automatically implement `convertType` and `getParsedValueClass`. You can find those interfaces in `io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholderTypes`

```java
package your.plugin.compat.mythicmobs.skills.placeholders.all;

import io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholder;
import io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholderTypes.StringPlaceholder;

import io.lumine.mythic.core.skills.placeholders.PlaceholderContext;
import javax.annotation.Nullable;

public class ExamplePlaceholder extends GenericPlaceholder<String> implements StringPlaceholder {
    
    public ExamplePlaceholder(GenericPlaceholderArguments metaContext) {
        super(metaContext);
    }

    @Nullable
    @Override
    public String applyWithMetaKeywords(PlaceholderContext placeholderContext) {
        return "hello world";
    }
}
```

---

## Step 5 - Use the `@MythicPlaceholder` annotation
This annotation will allow the placeholder to be registered by MythicMobs later
```java
package your.plugin.compat.mythicmobs.skills.placeholders.all;

import io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholder;
import io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholderTypes.StringPlaceholder;
import io.lumine.mythic.core.utils.annotations.MythicPlaceholder;

import io.lumine.mythic.core.skills.placeholders.PlaceholderContext;
import javax.annotation.Nullable;

@MythicPlaceholder(placeholder="example.placeholder")
public class ExamplePlaceholder extends GenericPlaceholder<String> implements StringPlaceholder {
    
    public ExamplePlaceholder(GenericPlaceholderArguments metaContext) {
        super(metaContext);
    }

    @Nullable
    @Override
    public String applyWithMetaKeywords(PlaceholderContext placeholderContext) {
        return "hello world";
    }
}
```


# Fetching Placeholder Arguments and Attributes

You can, optionally, fetch placeholder arguments (`<example.placeholder.argument1.argument.2>` or `<example.placeholder{argument1=hello;argument2=world}>`) using one of the following methods

- `GenericPlaceholder#getResolver` - The most complete one, but clunkier to use
- `GenericPlaceholder#getPlaceholder` - A less versatile, but more concise version
- `GenericPlaceholder#getPlaceholderString` - a very fast version made only for PlaceholderStrings

> [!warning]
> When you want to use placeholder arguments, you will have to also set a value for `usedPlaceholderArguments` in the `MythicPlaceholder` annotation

## Fetching an Attribute from the main MythicLineConfig
If you only need to fetch an attribute from the *main* configuration (and not from the one of a specific placeholder segment) you can just do the following
```java
    public NumericEntityScopedPlaceholder(EntityScopedPlaceholderArguments context, int rounding) {
        super(context);
        if(context.config == null) {
            return;
        }
        this.rounding = context.config.getInteger(new String[] {"rounding", "round", "r"}, rounding);
    }
```

## Simple Placeholder Argument
```java
package your.plugin.compat.mythicmobs.skills.placeholders.all;

import io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholder;
import io.lumine.mythic.core.skills.placeholders.types.GenericPlaceholderTypes.StringPlaceholder;
import io.lumine.mythic.core.utils.annotations.MythicPlaceholder;

import io.lumine.mythic.core.skills.placeholders.PlaceholderContext;
import javax.annotation.Nullable;

@MythicPlaceholder(placeholder="example.placeholder",usedPlaceholderArguments = 1)
public class ExamplePlaceholder extends GenericPlaceholder<String> implements StringPlaceholder {
    
    private final ResolvedPlaceholderSegment<PlaceholderString> argument;

    public ExamplePlaceholder(GenericPlaceholderArguments metaContext) {
        super(metaContext);
        this.argument = ...
    }

    @Nullable
    @Override
    public String applyWithMetaKeywords(PlaceholderContext placeholderContext) {
        return this.argument.get(placeholderContext);
    }
}
```

ResolvedPlaceholderSegment can be fetched in all of the following ways>

```java
                this.<String>getResolver()
                        .segIndex(0)
                        .segValueParser(PlaceholderString::of)
                        .build()
                        .get();
```
```java
                this.<String>getPlaceholder(0, SegmentSource.EXTRA_ARGS, null, PlaceholderString::of)
```
```java
                this.getPlaceholderString(0)
```

## Dynamic Amount of Used Arguments
If 
- The amount of arguments you will use is dynamic ("if there is an argument matching those conditions use it. Otherwise, default it to something else")
- You wish to use the MythicLineConfig syntax (`<example.placeholder{argument1=hello;argument2=world}>`)

You need to
- set `usedPlaceholderArguments` to a negative value (-1 works fine)
- call the `#initializeMetaKeywords` method at the end of the constructor

```java
@MythicPlaceholder(placeholder="utils.epoch",version="5.9", description="Returns the current epoch time in seconds", usedPlaceholderArguments = -1)
public class EpochPlaceholder extends GenericPlaceholder<Long> implements LongPlaceholder {

    private final ResolvedPlaceholderSegment<PlaceholderString> type;

    public EpochPlaceholder(GenericPlaceholderArguments metaContext) {
        super(metaContext);
        this.type = getPlaceholderString(0);
        initializeMetaKeywords();
    }

    @Nullable
    @Override
    public Long applyWithMetaKeywords(PlaceholderContext placeholderContext) {
        if (type.value() == null) {
            return Instant.now().getEpochSecond();
        }
        return switch (this.type.getOrDefault(placeholderContext, PlaceholderString::get, "seconds")) {
            case "millis" -> Instant.now().getLong(java.time.temporal.ChronoField.MILLI_OF_SECOND);
            case "ticks" -> Instant.now().getEpochSecond() * 20 + (Instant.now().getLong(java.time.temporal.ChronoField.MILLI_OF_SECOND) / 50);
            case "timestamp" -> Instant.now().toEpochMilli();
            default -> Instant.now().getEpochSecond();
        };
    }
}
```
> [!note]
> To use the MythicLineConfig Syntax, you must call either getPlaceholder or getResolver

## Using Wildcards Arguments
The placeholder name itself can have wildcard arguments. You can use and fetch those wildcard arguments in the following way
```java
@MythicPlaceholder(placeholder="skill.*.cooldown",usedPlaceholderArguments = -1)
public class SkillCooldownPlaceholder extends EntityScopedPlaceholder<Double> implements DoublePlaceholder {

    private final ResolvedPlaceholderSegment<PlaceholderString> skill;
    private Types type = Types.SECONDS;

    public SkillCooldownPlaceholder(EntityScopedPlaceholderArguments context) {
        super(context);
        this.skill = getPlaceholderString(0, SegmentSource.WILDCARD_ARGS);
        var cooldownType =
                this.<String>getResolver()
                        .mlcGetter(MythicLineConfig::getString)
                        .mlcAttributeAlias("type")
                        .segIndex(0)
                        .segValueParser((a) -> a)
                        .segValueChecker((s) -> s.equalsIgnoreCase("millis"))
                        .build()
                        .get();
        if (cooldownType.getValue() != null && cooldownType.getValue().equalsIgnoreCase("millis")) {
            this.type = Types.MILLIS;
        }
        initializeMetaKeywords();
    }

    enum Types {
        MILLIS,
        SECONDS
    }

    @Nullable
    @Override
    public Double applyToScope(PlaceholderContext placeholderContext) {
        if (this.type == null) {
            MythicLogger.debug(MythicLogger.DebugLevel.SKILL_INFO, "Placeholder " + this.instanceData.unparsedPlaceholder + " is invalid");
            return null;
        }

        final String skillName = this.skill.getOrDefault(placeholderContext, PlaceholderString::get, null);
        var maybeSkill = this.manager.getPlugin().getSkillManager().getSkill(skillName);

        if(maybeSkill.isEmpty()) {
            MythicLogger.debug(MythicLogger.DebugLevel.SKILL_INFO, "Placeholder " + this.instanceData.unparsedPlaceholder + " found no skill " + skillName);
            return null;
        }

        var skill = (MetaSkill) maybeSkill.get();

        SkillCaster entity = this.manager.getPlugin().getSkillManager().getCaster(this.getEntity.get(placeholderContext));

        return switch (type) {
            case MILLIS -> (skill.getCooldown(entity));
            default -> Numbers.round(skill.getCooldown(entity), 2);
        };
    }
}
```

# Other Kinds of GenericPlaceholder
Other than GenericPlaceholder, you can also inherit from
- `EntityScopedPlaceholder` - automatically prepends caster., target. etc. etc. to the placeholder name
- `NumericEntityScopedPlaceholder` - extends EntityScopedPlaceholder, while also automatically returning a Double value with a rounding attribute

## EntityScopedPlaceholder
This class allows you access to two very useful functions
- `getEntity.get(PlaceholderContext)` returns the AbstractEntity against which to parse the placeholder
- `getLocation.get(PlaceholderContext)` returns the AbstractLocation against which to parse the placeholder

> [!note]
> NumericEntityScopedPlaceholder inherits EntityScopedPlaceholder, and you can also use that one

```java
@MythicPlaceholder(placeholder="stance")
public class StancePlaceholder extends EntityScopedPlaceholder<String> implements StringPlaceholder {

    public StancePlaceholder(EntityScopedPlaceholderArguments arguments) {
        super(arguments);
    }

    @Nullable
    @Override
    public String applyToScope(PlaceholderContext placeholderContext) {
        if (this.getEntity.get(placeholderContext) instanceof ActiveMob am) {
            return am.getStance();
        }
        return null;
    }
}
```
```java
@MythicPlaceholder(placeholder="distance")
public class DistancePlaceholder extends NumericEntityScopedPlaceholder {


    public DistancePlaceholder(EntityScopedPlaceholderArguments context) {
        super(context);
    }

    @Nullable
    @Override
    public Number applyToScopeWithNumericFormatting(PlaceholderContext placeholderContext) {
        var caster = placeholderContext.meta().getCaster().getEntity().getLocation();
        var target = getLocation.get(placeholderContext);
        if (caster.getWorld().equals(target.getWorld())) {
            return caster.distance(target);
        }
        return null;
    }
}
```
> [!important]
> the `EntityScopedPlaceholder`'s constructor has a different signature from `GenericPlaceholder`'s. This is the only class inhereting `GenericPlaceholder` which can change the constructor signature! Don't go make new signatures on your own!
