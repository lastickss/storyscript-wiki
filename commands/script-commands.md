---
description: This page shows all the commands in the script file.
---

# 🔌 Script commands

`msg` – A message from the character.\
&#x20;             Usage: `msg "<personage>" <message>`.\
&#x20;             Example: `msg "John" Hello!`.\
&#x20;               Output: `[John] Hello!`

`setColor` – Setting the color of the personage's name.\
&#x20;                         Usage: `setColor "<color>"`.\
&#x20;                         Example: `setColor "red"`.

{% hint style="info" %}
**A note on setColor**

The color can be set either in hex format (#ffffff) or choose from 16 standard Minecraft colors. You can read them [here](https://htmlcolorcodes.com/minecraft-color-codes/).
{% endhint %}

`run` – Executing the standard Minecraft command.\
&#x20;             Usage: `run <command>`.\
&#x20;             Example: `run kill @a`.

`waitKey` – Waits for the [key](../misc/keys.md) to be pressed before executing the following script commands.\
&#x20;                       Usage: `waitKey`.

`sleep` – Waits for the specified time (in seconds) before executing the following commands.\
&#x20;                  Usage: `sleep <time>`.\
&#x20;                  Example: `sleep 5`.\
&#x20;                    Waits `5` seconds before executing the following commands.
