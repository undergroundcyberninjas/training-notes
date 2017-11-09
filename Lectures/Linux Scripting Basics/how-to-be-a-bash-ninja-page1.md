# How to be a Bash Ninja

This is a cheat sheet for the Bash shell. It applies both to the command line (interactive shell) use case and to scripting.

## Interactive Shell Cheat Sheet

Here are some commands that are useful when you're using the interactive shell.

- **``grep "string to search for"``:** Tool for searching and manipulating strings of text. Simple to use, but also very expandable (Google it).
- **``ls``:** Lists contents of the directory
- **``touch /path/to/file``:** Creates an empty file
- **``echo "your string of text"``:** Writes a string of text (or a variable) to the console. Very useful with pipes and redirects.
- **``cat /path/to/file``:** Prints the contents of a file to the console. Also very useful with pipes and redirects, and in conjunction with ``grep``.
- **``pwd``:** Prints working directory (i.e. where you are right now)
- **``lsblk``:** Lists all connected disks (not useful in cyberpatriot, but useful in reality)
- **``netcat -tulpn``:** Lists processes listening on ports
- **``mv /path/to/file.txt /path/to/file-renamed.txt``:** Move a file, also doubles as a renaming tool
- **``wget http://example.com/some/link/to/file.zip``:** Download a webpage or a file via HTTP
- **``more``:** Use to pipe long command output into to make it scrollable. Ex: ``ls -l | more``

## ``&&`` Operator

This is a simple, but essential tool, especially for speeding things up at the interactive shell. It simply combines two separate commands and runs them one after the other.

For example, normally upgrading system packages requires you to run both ``sudo apt-get update`` and ``sudo apt-get upgrade``, one after the other. Instead, run:
```
sudo apt-get update && sudo apt-get upgrade -y
```

The shell will run ``sudo apt-get update``, then when that's done, it will run ``sudo apt-get upgrade -y`` (the ``-y`` just tells APT to automatically say yes to downloading the upgrades). This is a great one-liner to save yourself some time in CyberPatriot.
