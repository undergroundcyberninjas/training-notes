# Scripting Basics

### Shells

We've all used the **command line** on Windows and Linux. But how does it work? Here are important things you need to know about the command line.

- Commands are interpreted by a **shell**
- One operating system can have multiple shells available
- **Common Linux Shells:**
	- **Bash:** most popular; this is the command line you're familiar with)
	- **Sh:** also very popular
	- **Csh:** shell based on the C language
	- **Zsh:** a more modern shell
- Common Windows Shells
	- **Command Prompt:** a DOS-centric shell
	- **PowerShell:** Microsoft's answer to more powerful, modern shells like Bash

### What is a Script?

A script, basically, is a list of commands for a shell to carry out. Most shells support simple IF/ELSE statements, loops, and other typical programming language features, although the syntax of a shell script is usually much less intuitive than modern languages like Python.

Let's look at an example of a Bash script.

```
#!/bin/bash

# The Super Useful Bash Script
# Author: Joe Bag of Donuts

if [ $1 -gt 100 ]
then
	echo "Number greater than 100. Listing current working directory contents..."
	ls
fi

echo "Commands complete at:"
date
```