---
description: On this page, the syntax of the StoryScript script files will be explained.
---

# 🖥️ The syntax of the script files

The syntax `.sscript` is pretty simple. Each line in the file is a new command.

Вот пример файла `.sscript`, который выводит в чат сообщение `[Валера] Привет! Как у тебя дела?`:\
Here is an example of a `.sscript` file that outputs a message to the chat `[John] Hi! How are you?`:

{% code title="Test.sscript" lineNumbers="true" %}
```
msg "John" Hi! How are you?
```
{% endcode %}

You can also make comments in the script files using `//`:

{% code title="Test.sscript" lineNumbers="true" %}
```
// Welcome
msg "John" Hi! How are you?
// End of the script
```
{% endcode %}
