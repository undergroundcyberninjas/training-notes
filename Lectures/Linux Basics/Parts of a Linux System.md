# Parts of a Linux System

These notes cover the parts of a Linux system, in (approximately) the order they start up. This includes:

- GRUB Bootloader
- Linux Kernel
- init/background services
- Package Managers (specifically for Debian, so ``apt-get`` and ``dpkg``)
- Basic Command-Line Tools (such as GNU Nano, ``ls``, and others)

---


## Key Terms/Programs
- **Kernel** - The core part of the operating system which interfaces directly with hardware. It is the first thing that boots.
- **GRUB Bootloader** - The really really tiny program that starts the Linux kernel and passes it the right bootup parameters.
- **``init``** - Program that runs on startup and manages all the  background processes in Linux.
- **Daemons** - Programs that run in the background (such as an SSH server)
- **Shell** - Program that accepts commands/input from the user to run other programs. The most common shells are BASH and SH, located in ``/bin/bash`` and ``/bin/sh``, respectively.
- **Console** or **Terminal** - Another word for the Linux command prompt; usually implied to mean the BASH shell.
- **Package** - A premade "bundle" for installing a program easily on a Linux system. This differs _a lot_ from the Windows method to install things. On Ubuntu, these packages are ``.deb`` files.
- **Package Manager** - Program to install packages. This usually means one of two things: ``dpkg`` or ``apt-get``.
- **``dpkg``** - Command-line tool for installing ``.deb`` packages
- **APT** - System for easy downloading, installing, and updating of packages via APT repositories on the Internet. APT is an example of a package manager.
- **``apt-get``** - Command-line tool for using APT

---

# The Linux Boot Process
1. Your computer starts up and the BIOS goes through POST.
2. After POST, the BIOS looks at the Master Boot Record (MBR) and loads the first bootable portion of the hard drive: GRUB.
3. GRUB presents you with a menu from which you boot Linux. GRUB passes very basic information to the Linux kernel about starting (you can press ``e`` at the GRUB menu to edit this)
4. The Linux kernel boots:
	- Loads itself and some other uber-important stuff into RAM
	- Mounts filesystems
	- Starts ``init``, which starts up all your background services
	- _Sometimes, all this is hidden by a splash screen, but that's usually only on desktop Linux distributions. You can often disable this by editing your GRUB config._
5. Once ``init`` has started up all your system's daemons, you are dropped to a login screen (or your display manager, the GUI equivalent of a login prompt).

## After Login
On a system without a desktop environment, once you log in, Linux runs the shell. By default, this is the BASH shell, located in ``/bin/bash``. It gives you a prompt like this:

```
you@your-machine-hostname:~$
```
You are now at the Linux command line.

# Conquering the Console

Now that you're at the console, you can do stuff on your Linux system.

### Working Directory

When you are using a shell, you are always operating from a specific directory, called your **working directory.** When you first log in, this is usually your home directory, represented by ``~`` for short. To change your working directory, use the ``cd`` command like in the example below.

```
hampton@laptop:~$ cd /etc/libreoffice
hampton@laptop:/etc/libreoffice$ 
```

I changed from my home directory (where I was originally) to ``/etc/libreoffice``. You can ``cd`` to any directory you want (as long as you have permission to access it.

### The List Command : ``ls``

If you need to know what files/folders are inside your working directory, you can run ``ls``. It prints a list of everything in your directory (or another directory, if you specify one).

```
