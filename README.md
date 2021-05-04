# Disguise Lib

A server-side library that allows disguising entities as other ones.
~~Features built-in `/disguise` command as well.~~
[`/disguise` command with some other features has been moved to a separate mod.](https://github.com/samolego/MobDisguises)

## Dependecy
```gradle
repositories {
	maven {
		url 'https://maven.nucleoid.xyz'
	}
	// OR
	maven {
        url 'https://jitpack.io'
    }
}

dependencies {
    // fabric
    modImplementation "xyz.nucleoid:DisguiseLib:${project.disguiselib_version}"
  
    // jitpack - architectury
        // Architectury (common module)
    modImplementation "xyz.nucleoid:DisguiseLib:disguiselib:${project.disguiselib_version}"
    
    // Fabric
    modImplementation "xyz.nucleoid:DisguiseLib:disguiselib-fabric:${project.disguiselib_version}"
    
    // Forge
    implementation fg.deobf "xyz.nucleoid:DisguiseLib:disguiselib:${project.disguiselib_version}"
  
}
```
# API

Use the provided interface `EntityDisguise` on any class extending `net.minecraft.entity.Entity`.

```java
import xyz.nucleoid.disguiselib.casts.EntityDisguise;

import net.minecraft.entity.Entity;
import net.minecraft.entity.EntityType;

public class MyDisguises {
    public static void disguise() {
        // Disguises as creeper
        ((EntityDisguise) entityToDisguise).disguiseAs(EntityType.CREEPER);

        // Disguise as aCustomEntity (net.minecraft.entity)
        ((EntityDisguise) entityToDisguise).disguiseAs(aCustomEntity);

        // If you disguise it as EntityType.PLAYER, you can apply custom GameProfile as well
        ((EntityDisguise) entityToDisguise).setGameProfile(aCustomGameProfile);

        ((EntityDisguise) entityToDisguise).isDisguised(); // Tells whether entity is disguised or not
        ((EntityDisguise) entityToDisguise).removeDisguise(); // Clears the disguise

        
        // Not that useful (mainly for internal use)
        ((EntityDisguise) entityToDisguise).getDisguiseType(); // Gets the EntityType of the disguise
        ((EntityDisguise) entityToDisguise).disguiseAlive(); // Whether the entity from the disguise is an instance of LivingEntity
    }    
}

```

