---
description: This page shows all the commands in the script file.
---

# 🔌 Script commands

### Execution & Flow

* sleep – Pauses script execution for a specified duration.
  * Usage: `sleep <seconds>`
  * Example: `sleep 2.5`
  * Note: Supports fractional seconds (e.g., `2.5`).
* run – Executes a standard Minecraft command.
  * Usage: `run <command>`
  * Example: `run kill @a`

### Output & Visuals

* msg – A message from the character.
  * Usage: `msg <personage> <message>`
  * Example: `msg John Hello!` or `msg "NPC $$playerName" "The prophecy is true!"`
  * Output: `[John] Hello!`
  * Note: Quotes are now optional for single-word personages or messages. Variable placeholders (`$$variable`) are fully supported in the personage's name.
* setColor – Sets the color of the personage's name.
  * Usage: `setColor <color>`
  * Example: `setColor red`
  * Note: The color can be set either in hex format (`#ffffff`) or chosen from 16 standard Minecraft colors.
* setMessageColor – Sets the color of the message text.
  * Usage: `setMessageColor <color>`
  * Example: `setMessageColor #aaffaaff`

### Variables

* setVar – Sets a local (temporary) variable.
  * Usage: `setVar <variable name> <variable value>`
  * Example: `setVar playerName John`
  * Note: This variable is only stored in memory while the script is actively running.
* setGlobal – Sets a global (world-persistent) variable.
  * Usage: `setGlobal <variable name> <variable value>`
  * Example: `setGlobal quest_status 2`
  * Note: This value is saved to the world's storage and persists across server restarts.
* Variable Usage: You can get the value of any variable (local or global) in the `msg` command using `$$<variable name>`.
  * Example: `msg "NPC" His name is $$playerName.`
