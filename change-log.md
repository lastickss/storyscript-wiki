# 🆕 Change log

## 0.2+1.21.1

***

* Migrated the mod to Minecraft 1.21.1.
* Complete code refactoring performed.
* Reworked the script execution engine to a stable, tick-based system to fix all timing and instant execution bugs.
* Critical Fix: The `sleep` command no longer ignores the pause and correctly delays the script execution.
* The `sleep` command now supports fractional time values (e.g., `sleep 0.5`).
* Added console command `/sscript setglobal` to manage world variables.
* Fixed variable placeholders (`$$var`) not being parsed in the character name part of the `msg` command.
* Introduced the [IScriptCommand API](for-developers/iscriptcommand-api.md) for developers to easily add custom commands.

## 0.1.1+1.20.4

***

* Added a test interface that displays the mod version (opens with `/sscript` command).
* Added script command `sleep <number of seconds>` , which waits for some time before executing the next command.
* Now when a script error occurs, the line where the error occurred is displayed.

## 0.1-1.20.4

***

* Added creation of sscripts folder in the root folder of the game.
* Added scripts reading system
* Added `msg` script command
* Added `setColor` script command
* Added `setVar` script command
* Added `run` script command
* Added variable system
* Added `$$variableName` to replace a variable in the msg command
