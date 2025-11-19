# IScriptCommand API

The StoryScript API allows developers to easily extend the scripting language by creating custom commands. This guide explains how to define and register your own command using the `IScriptCommand` interface.

### Prerequisites

To create custom commands, you need access to the following classes from the StoryScript mod:

<table data-header-hidden data-full-width="false"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Class</strong></td><td><strong>Package</strong></td><td><strong>Purpose</strong></td></tr><tr><td><code>IScriptCommand</code></td><td><code>com.lasticks.storyscript.api</code></td><td>The interface your command class must implement.</td></tr><tr><td><code>ScriptContext</code></td><td><code>com.lasticks.storyscript.api</code></td><td>Provides access to the server, source, variables, and script controls (<code>sleep</code>, <code>setvar</code>).</td></tr><tr><td><code>ScriptCommandRegistry</code></td><td><code>com.lasticks.storyscript.registry</code></td><td>Used to register your command name with the Script Engine.</td></tr></tbody></table>

### 1. Creating th Command Class

Your custom command must implement the `IScriptCommand` interface, which requires a single method: `execute()`.

Example: The `HEAL` Command

```java
package com.yourmod.storyscript.commands;

import com.lasticks.storyscript.api.IScriptCommand;
import com.lasticks.storyscript.api.ScriptContext;
import net.minecraft.server.network.ServerPlayerEntity;

public class HealCommand implements IScriptCommand {

    @Override
    public void execute(ScriptContext ctx, String[] args) {
        
        // 1. Get the player (the command source)
        ServerPlayerEntity player = ctx.getSource().getPlayer();

        // Check if the source is a player (not the console)
        if (player != null) {
            
            // 2. Execute the action
            player.setHealth(player.getMaxHealth());
            player.getHungerManager().setFoodLevel(20);
            
            // 3. Provide feedback (optional)
            ctx.sendMessage("You feel refreshed!");

        } else {
            // Handle if the command was run by console
            ctx.sendError("The HEAL command can only be used by players.");
        }
        
        // Note: Commands should execute instantly. 
        // If you need a pause, use: ctx.sleep(seconds);
    }
}
```

### 2. Registering the Command

Once your command class is ready, you must register it with the `ScriptCommandRegistry` so the Script Engine knows which class to execute when it encounters the command name in a script file.

You should perform the registration during your mod's main initialization (`onInitialize`).

#### Example: Mod Initialization

```java
package com.yourmod;

import com.lasticks.storyscript.registry.ScriptCommandRegistry;
import com.yourmod.storyscript.commands.HealCommand;
import net.fabricmc.api.ModInitializer;

public class YourStoryScriptExtension implements ModInitializer {

    @Override
    public void onInitialize() {
        
        // Register the new command!
        // The first argument is the command name used in the .sscript file.
        // The second argument is an instance of your command class.
        
        ScriptCommandRegistry.register("heal", new HealCommand());
        
        // You can register multiple commands:
        // ScriptCommandRegistry.register("giveitem", new GiveItemCommand());
    }
}
```

### 3. Usage in Script Files

After successful registration, players can use your new command in their script files (`.sscript`):

```
// The player runs a script that calls your new command
msg System "A wild NPC appeared and granted you power!"
sleep 2
heal // <-- Calls your registered command
msg System "You are now at full health!"
```

### Argument Handling

The `String[] args` array passed to the `execute()` method contains all words and quoted phrases following the command name.

| **Script Line**           | **commandName** | **args content**          |
| ------------------------- | --------------- | ------------------------- |
| `heal`                    | `"heal"`        | `{}` (empty array)        |
| `heal target_player`      | `"heal"`        | `{"target_player"}`       |
| `heal 10 "diamond sword"` | `"heal"`        | `{"10", "diamond sword"}` |

It is the responsibility of your `execute()` method to validate the length and type (e.g., parse strings to integers) of the `args` array.

### 4. Key Context Methods

The `ScriptContext` object is your gateway to all necessary server functions:

| **Method**                        | **Description**                                            |
| --------------------------------- | ---------------------------------------------------------- |
| `ctx.getServer()`                 | Returns the main `MinecraftServer` instance.               |
| `ctx.getSource()`                 | Returns the `ServerCommandSource` that started the script. |
| `ctx.getVar(key)`                 | Gets a local variable (`$var`) value.                      |
| `ctx.setVar(key, value)`          | Sets a local variable (`$var`) value.                      |
| `ctx.sleep(double seconds)`       | Pauses the script for the given duration (in seconds).     |
| `ctx.sendMessage(String message)` | Sends a simple message to the command source.              |
| `ctx.sendError(String message)`   | Sends an error message to the command source.              |

