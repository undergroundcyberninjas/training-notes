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