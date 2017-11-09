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

# How to be a Bash Ninja (page 2)

## Pipes

A **pipe** lets you pass the output of one command in as the input for another command. For example, to run ``command-one`` and pass its output to ``command-two``, use this:
```
command-one | command-two
```

One of the best ways to use this is with grep. For example, to quickly search a file for the string ``"nonoptimal"``, you could use:
```
cat /path/to/my/file.txt | grep "nonoptimal"
```
This will use the ``cat`` command to pass the entire contents of the file as the input to ``grep``, and ``grep`` will search for the string ``nonoptimal`` and then print _only_ the line(s) that contain ``nonoptimal``.



## Redirects

A **redirect** lets you pass the output of a command into a file, or pass a file in as input to a command.

There are three things you can manipulate with a redirect:
- **Standard Output (stdout, uses ``>`` or ``1>``:** This is the main output of the command. For example, the directory listing of ``ls`` would be on stdout.
- **Standard Error (stderr, uses ``2>``):** This is the output for errors. If something goes wrong with your command, it will end up here. For example, if you tried to run ``ls`` in a directory you don't have permission to read, you'd see information on stderr.
- **Standard Input (stdin, uses ``<``):** This allows you to pass things in as the input of a command.

Redirects can get very complicated, but a simple example is:

```
echo "Super cool stuff to go in my text file!" > /path/to/nice-text-file.txt
```

This will create a new text file and put ``Super cool stuff to go in my text file!`` inside.

For more information on redirects, you can start here, or just Google it: http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html
