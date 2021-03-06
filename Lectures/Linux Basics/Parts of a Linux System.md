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
- **Master Boot Record** - The really really tiny part (512 bytes) at the beginning of your hard drive that tells your computer about the partitioning
- **GRUB Bootloader** - The really really tiny program that starts the Linux kernel and passes it the right bootup parameters.
- **``init``** - Program that runs on startup and manages all the  background processes in Linux.
- **Daemons** - Programs that run in the background (such as an SSH server)
- **PAM** - Pluggable Authentication Modules, used for logon/applications. Do not control permissions, only authentication
- **Shell** - Program that accepts commands/input from the user to run other programs. The most common shells are BASH and SH, located in ``/bin/bash`` and ``/bin/sh``, respectively.
- **Console** or **Terminal** - Another word for the Linux command prompt; usually implied to mean the BASH shell.
- **Package** - A premade "bundle" for installing a program easily on a Linux system. This differs _a lot_ from the Windows method to install things. On Ubuntu, these packages are ``.deb`` files.
- **Package Manager** - Program to install packages. This usually means one of two things: ``dpkg`` or ``apt-get``.
- **``dpkg``** - Command-line tool for installing ``.deb`` packages
- **APT** - System for easy downloading, installing, and updating of packages via APT repositories on the Internet. APT is an example of a package manager.
- **``apt-get``** - Command-line tool for using APT
- **repository** - A central place where ``.deb`` packages and other package info is stored so APT can fetch them
- **dependencies** - Other packages that a given software needs to run
- **flag** - a command-line argument. For example, ``-all`` is a common flag for the ``ls`` command.

---

# The Linux Boot Process
1. Your computer starts up and the BIOS goes through POST.
2. After POST, the BIOS looks at the **Master Boot Record (MBR)** and loads the first bootable portion of the hard drive: **GRUB**.
3. GRUB presents you with a menu from which you boot Linux. GRUB passes very basic information to the Linux kernel about starting (you can press ``e`` at the GRUB menu to edit this)
4. The Linux kernel boots:
	- Loads itself and some other uber-important stuff into RAM
	- Mounts filesystems
	- Starts ``init``, which starts up all your background services. ``init`` is configured in ``/etc/init`` and ``/etc/init.d``.
	- _Sometimes, all this is hidden by a splash screen, but that's usually only on desktop Linux distributions. You can often disable this by editing your GRUB config._
5. Once ``init`` has started up all your system's daemons, you are dropped to a login screen (or your display manager, the GUI equivalent of a login prompt).
6. When you log in, your credentials go through PAM to make sure you are who you say you are, then Linux moves on to the shell.

## After Login
On a system without a desktop environment, once you log in, Linux runs the shell. By default, this is the BASH shell, located in ``/bin/bash``. There are other shells, but BASH is the one 90% of Linux systems use. It gives you a prompt like this:

```
you@your-machine-hostname:~$
```
You are now at the Linux command line.

# Conquering the Console

Now that you're at the console, you can do stuff on your Linux system.

### Working Directory

When you are using a shell, you are always operating from a specific directory, called your **working directory.** When you first log in, this is usually your home directory, represented by ``~`` for short. To change your working directory, use the ``cd`` command like in the example below.

```
cyberpatriot@demo-1:~$ cd /etc/libreoffice
cyberpatriot@demo-1:/etc/libreoffice$ 
```

I changed from my home directory (where I was originally) to ``/etc/libreoffice``. You can ``cd`` to any directory you want (as long as you have permission to access it. If you need to know where your current working directory is, you can run ``pwd``, which stands for "print working directory."

#### Aliases

There are a couple shorthand directories at the Linux command line:

- ``.`` Current Directory
- ``..`` Parent Directory
- ``~`` Your user's home directory

Let's say we're in ``/etc/libreoffice`` and we want to change back to our home directory. We could do this:

```
cyberpatriot@demo-1:~$ cd ~
cyberpatriot@demo-1:~$ 
```

Now we're in ``/home/cyberpatriot``. But maybe we want to be in ``/home/cyberpatriot/exampleFolder``. How do we get there from here?

```
cyberpatriot@demo-1:~$ cd ./someFolder
cyberpatriot@demo-1:~/someFolder$
```

Finally, let's say we want to go up one directory (back into /home/cyberpatriot) from ``~/someFolder``.

```
cyberpatriot@demo-1:~/someFolder$ cd ..
cyberpatriot@demo-1:~$
```

Just to make sure we are where we think we are, we can run ``pwd``.

```
cyberpatriot@demo-1:~$ pwd
/home/cyberpatriot
```

That's it! Don't forget these commands. They are absolutely irreplaceable for getting around a Linux system.

### The List Command : ``ls``

If you need to know what files/folders are inside your working directory, you can run ``ls``. It prints a list of everything in your directory (or another directory, if you specify one).

```
cyberpatriot@demo-1:~$ ls
cmatrix_1.2a-5_amd64.deb      super-cool-script.sh      someFolder
```

``ls`` also has some optional parameters you can pass to it. For example, let's say we wanted to see the permissions information and the date the files were modified, and we wanted to show hidden files. We can run ``ls`` with the ``-all`` **flag**, like so:

```
cyberpatriot@demo-1:~$ ls -all
total 53
drwxr-xr-x+ 4 cyberpatriot cyberpatriot     8 Mar 29 14:20 .
drwxr-xr-x+ 3 root         root             3 Mar 29 13:35 ..
-rw-r--r--  1 cyberpatriot cyberpatriot   220 Mar 29 13:35 .bash_logout
-rw-r--r--  1 cyberpatriot cyberpatriot  3637 Mar 29 13:35 .bashrc
drwx------+ 2 cyberpatriot cyberpatriot     3 Mar 29 13:36 .cache
-rw-r--r--  1 cyberpatriot cyberpatriot   675 Mar 29 13:35 .profile
-rw-r--r--  1 cyberpatriot cyberpatriot 16636 Apr 12  2014 cmatrix_1.2a-5_amd64.deb
drwxr-xr-x+ 2 cyberpatriot cyberpatriot     3 Mar 29 14:20 mytextfiles
```

### ``man`` Pages

You can imagine it gets complicated to remember all the arguments and flags for every command. There are hundreds of commands, so what if you forget something?

Man pages are here to help. You can run ``man <software name>`` and get a manual page about it. For example, for the manual page about using ``man``, you'd run:
```
cyberpatriot@demo-1:~$ man man
```

Which gets you this:

![](http://www.basicconfig.com/files/imagepicker/j/jinlusuh/man_screenshot01.png)

Can you open the man page for ``ls``?

### Using the GNU Nano text editor

Most configuration files at the command line are just plain text files, so it is _very_ important that you know how to use a text editor at the Linux command line. There are many text editors available, with the two most notable being VIM and Nano. VIM is a very advanced, powerful editor, so we'll get into that later. Nano is a simple editor with basic features. Let's edit a text file with nano.

1. First we'll use ``ls`` to find the filename we want to edit. We already know the file is in the folder ``/home/cyberpatriot/mytextfiles``, so we'll ``cd`` there.

```
cyberpatriot@demo-1:~$ ls
cmatrix_1.2a-5_amd64.deb
mytextfiles
cyberpatriot@demo-1:~$ cd ./mytextfiles
cyberpatriot@demo-1:~/mytextfiles$ ls
some-file.txt
cyberpatriot@demo-1:~$
```

Now we know the file name, so let's open it with ``nano``.

```
cyberpatriot@demo-1:~$ nano ./some-file.txt
```

_Recognize the ``./`` in the path above?_

And now you're at a text editor. It's very simple to use as long as you know that the ``^`` character in all the shortcuts represents the CTRL key. So to save and exit, you'd press CTRL+X (then Y for yes, and ENTER, following the prompts on your screen). Pretty simple!

_Note: You can also open a file with nano with the full path. For example, we could have run ``nano /home/cyberpatriot/mytextfiles/some-file.txt`` in the example above. We just used the ``.`` relative path to save keystrokes._

## Installing Packages

There are two ways to install packages on an Ubuntu system: ``dpkg`` and APT.

### Installing and removing software with ``dpkg``

``dpkg`` takes a ``.deb`` file on your hard drive and installs it, and it does _not_ have any updating functionality. It can install and remove packages, but does not automatically fetch **dependencies**. This can be remedied with APT later on. Let's look at a demo of ``dpkg``:

```
cyberpatriot@demo-1:~$ sudo dpkg --install cmatrix_1.2a-5_amd64.deb
Selecting previously unselected package cmatrix.
(Reading database ... 17008 files and directories currently installed.)
Preparing to unpack cmatrix_1.2a-5_amd64.deb ...
Unpacking cmatrix (1.2a-5) ...
Setting up cmatrix (1.2a-5) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
```
Now we can run the ``cmatrix`` program. If we want to remove it, we use the package name, ``cmatrix``, not ``cmatrix_1.2a-5_amd64.deb``. So removing it looks like this:

```
cyberpatriot@demo-1:~$ sudo dpkg --remove cmatrix
(Reading database ... 17018 files and directories currently installed.)
Removing cmatrix (1.2a-5) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
```

Now ``dpkg`` is great for simple things, but what if you want updating functionality? What if your package has **dependencies**, other packages that are required for it to run? That's where APT comes in.

### Managing packages with APT

#### Repositories and the sources.list file

APT still uses ``.deb`` files under the hood, but it fetches them from **repositories,** servers accessed via HTTP or FTP that store ``.deb`` packages. Most distributions of Linux maintain their own "general use" repositories, which come enabled by default, but you can also add your own third-party repositories. The list of APT repositories is stored in ``/etc/apt/sources.list`` and sometimes also in the folder ``/etc/apt/sources.list.d/``. Let's open ``/etc/apt/sources.list`` with ``nano``. Don't be alarmed about the colors, that's just nano's built-in syntax highlighting.

```
cyberpatriot@demo-1:~$ nano /etc/apt/sources.list
```

![](https://raw.githubusercontent.com/bhscyberninjas/training-notes/master/Images/sources.list-screenshot.png)

_Note: See how ``nano`` is warning us we don't have write permission? How could we fix that if we wanted to write to the file instead of just reading it?_

So we have only the three default repositories enabled on our system right now. If you wanted to add a repository for Webmin, for example, you might add: ``deb http://download.webmin.com/download/repository sarge contrib`` to the ``sources.list`` file. Then you could save it and run ``apt-get update`` and you'd be able to install software from that repository.

#### Updating APT package lists

Arguably the most important APT command is ``apt-get update``, which fetches updated information on packages. It doesn't install anything, it just goes and finds out what packages need updates, what you can and can't install, etc. It requires root access, so prefix it with ``sudo``.

```
cyberpatriot@demo-1:~$ sudo apt-get update
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]
Get:2 http://archive.ubuntu.com trusty-security InRelease [65.9 kB]
Hit http://archive.ubuntu.com trusty Release.gpg
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-security/main Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty-security/universe Translation-en
Hit http://archive.ubuntu.com trusty Release
Hit http://archive.ubuntu.com trusty/main amd64 Packages
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en
Fetched 132 kB in 3s (36.3 kB/s)
Reading package lists...
cyberpatriot@demo-1:~$
```

_Do you see it fetching stuff from the repositories in ``sources.list``?_

Now APT has all the latest information about all our packages.

#### Installing Packages

Let's install something. In this example, we're going to install an SSH server package. You can usually find a package name on Google, but I already know that this package is called ``openssh-server``. So let's install it! Be sure to run ``apt-get update`` if you haven't run it recently; it's always a good idea to keep package info up to date.

```
cyberpatriot@demo-1:~$ sudo apt-get update
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]
Get:2 http://archive.ubuntu.com trusty-security InRelease [65.9 kB]
Hit http://archive.ubuntu.com trusty Release.gpg
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-security/main Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty-security/universe Translation-en
Hit http://archive.ubuntu.com trusty Release
Hit http://archive.ubuntu.com trusty/main amd64 Packages
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en
Fetched 132 kB in 3s (36.3 kB/s)
Reading package lists...
cyberpatriot@demo-1:~$ sudo apt-get install openssh-server
```

It will give you a bunch of information, including a list of dependencies needed, and the amount of disk space the program requires. If you are okay with this, type ``y`` for yes and press ENTER.

Once the command finishes, it should be installed. That's it! Installing packages with APT is that simple!

## APT/dpkg Cheat Sheet

When in doubt, consult Google or the ``man`` page, but here are some of the most common APT tasks (``<package-name>`` represents a package name _without_ the ``<>``):

| Task                                          	| Command                                   	| Description                                                                                                                                                                                                       	|
|-----------------------------------------------	|-------------------------------------------	|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| **Upgrade**                                       	| ``apt-get upgrade``                       	| Updates the _actual packages_, but should usually be run _after_ ``apt-get update``.                                                                                                                              	|
| **Update**                                        	| ``apt-get update``                        	| Updates _information_ about packages, not the actual packages.                                                                                                                                                    	|
| **Fix Missing Dependencies**                      	| ``apt-get install -f```                   	| Checks to see if you have any dependencies missing and fixes them. Useful if APT crashed or was killed unexpectedly during a package install. Also useful when you've installed a ``.deb`` that has dependencies. 	|
| **Install**                                       	| ``apt-get install <package-name>``        	| Installs package named ``<package-name>``                                                                                                                                                                         	|
| **Uninstall and Purge**                           	| ``apt-get remove --purge <package-name>`` 	| Uninstalls ``<package-name>`` and deletes any cached package files from your computer. _Does not remove dependencies!_                                                                                            	|
| **Automatically Remove Unnecessary Dependencies** 	| ``apt-get autoremove --purge``            	| Removes any dependencies and deletes and cached package files from your computer.                                                                                                                                 	|
| **Setup Again**                                   	| ``dpkg-reconfigure <package-name>``       	| Goes through the package's initial setup again. Useful if you accidentally put in something wrong when you set it up, or if you broke a configuration really badly and need to start over.                        	|
| **Install from .deb**                             	| ``dpkg -i /path/to/file.deb``             	| Installs ``/path/to/file.deb`` to your system. Does _not_ automatically fetch dependencies like APT, so you'll need to run ``apt-get install -f`` to fix that.                                                    	|
