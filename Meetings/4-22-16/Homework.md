# BHS CyberPatriot
### 4/22/16 - Homework

This homework assignment focuses on file permissions, basic Linux commands, and users/groups.

1. In a new Ubuntu Server VM (no GUI, only command line), create a user called ``cyberpatriot``.

2. In ``cyberpatriot``'s home directory, make a new directory called ``homework``
3. In the ``homework`` directory, create a new file called ``theforce``.

4. Using a text editor, add the following to your new file, ``theforce``:

    ```
    #!/bin/bash
    echo The motion picture will begin in a moment.
    sleep 4
    telnet towel.blinkenlights.nl
    ```
    
5. Install the APT package ``telnet``. *If we haven't covered package management, the command to install the package named ``telnet`` is ``apt-get install telnet``, but it requires root priveleges, so prefix it with ``sudo``.*

6. Give the user ``cyberpatriot`` permission to read, write, and execute the file ``theforce``.

7. Make a new group called ``jedi`` and give the group permission to read/execute ``theforce``. Make sure they do not have permission to write.
8. Give ``other`` (aka "the world") permission to read ``theforce`` but *not* execute or write permission.
9. Execute the script ``theforce`` by running ``./theforce`` from inside the ``homework`` folder (``/home/cyberpatriot/homework``).
10. If it works, you should get an ASCII text movie on your screen.
11. When you've had enough, you can quit watching and exit the telnet session by holding ``CTRL`` and ``]``. This should give you a prompt like this:

``telnet>``

Type ``close`` at the prompt and press enter. That should exit out of the telnet session.