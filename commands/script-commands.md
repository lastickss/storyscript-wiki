---
description: This page shows all the commands in the script file.
---

# 🔌 Script commands

`msg` – A message from the character.\
&#x20;             Usage: `msg "<personage>" <message>`.\
&#x20;             Example: `msg "John" Hello!`.\
&#x20;               Output: `[John] Hello!`

`setColor` – Setting the color of the personage's name.\
&#x20;                         Usage: `setColor <color>`.\
&#x20;                         Example: `setColor red`.

{% hint style="info" %}
**A note on setColor**

The color can be set either in hex format (#ffffff) or choose from 16 standard Minecraft colors. You can read them [here](https://htmlcolorcodes.com/minecraft-color-codes/).
{% endhint %}

`run` – Executing the standard Minecraft command.\
&#x20;             Usage: `run <command>`.\
&#x20;             Example: `run kill @a`.

`setVar` – sets the variable.\
&#x20;             Usage: `setVar <variable name> <variable value>`\
&#x20;             Example: `setVar playerName John`

You can also get the value of a variable in the msg command using `$$<variable name>`.\
&#x20;             Example: `msg "NPC" His name is $$playerName`.
