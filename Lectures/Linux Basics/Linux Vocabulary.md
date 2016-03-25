# Linux Vocabulary:

- **APT** - The package manager for Debian-based distributions, including Ubuntu.

- **Distribution [distro]** - A particular "bundled" version of Linux. There are many different distros with many different intended purposes, ranging from large general-purpose distros like Debian, Ubuntu, and Fedora to very specific distros such as Untangle, a Debian-based router/firewall distro.

- **Directory [folder]** - Folders are technically called "directories" in Linux, but both terms are used interchangeably.

- **Kernel** - The kernel is the core part of an operating system. It acts as an interface from the bare metal (the hardware, such as your CPU and motherboard) to the rest of the OS. On a Linux system, you are running the Linux Kernel. Windows and OSX have kernels too (such as the Windows NT kernel), but since they are closed-source and not changeable like Linux, they are seldom discussed.

- **Shell** - The program that takes commands from the user to execute other programs. In Linux, the most common shells are the BASH shell and the SH shell. In Windows, there is the Command Prompt and Windows PowerShell.

- **Root Directory ``/``** - The top of the Linux directory tree. Everything is contained inside of the root directory, which is represented by a ``/``.

- **Terminal [console, command-line, CLI]** - Common name for the Linux command line, either in a window or on a text-mode-only system that does not have a desktop environment.

- **Desktop Environment [DE]** - The part of Linux that handles your graphical programs, how windows are drawn/placed, and other GUI-related things. Examples include Ubuntu Unity, GNOME, KDE, XFCE, and LXDE.

- **Display Manager [dm]** - The graphical program that comes up before your desktop environment and handles logging in. This is usually bundled with a desktop environment. For example, the GNOME desktop uses the ``gdm`` display manager.

- **Package Manager** - *This is very different from Windows!* The command-line program that handles installing software in Linux. There are often GUIs bundled for using a package manager, such as Synaptic, but the actual action happens at the command line. Most distributions come bundled with a package manager and basic repositories maintained by the distro. Ubuntu uses APT, which uses ``.deb`` package files. Other distros like Fedora use ``yum`` or others. Most software is available through package repositories, though some less-known programs require compiling and installing yourself.

- **Package Repositories [repos]** - Essentially "app stores" for your package manager to fetch and install software from. Linux distributions usually come with some repositories maintained by the distribution's developers, which contain most software. However, you can also add third-party repositories if you want. For APT, this is done by editing the APT sources file at ``/etc/apt/sources.list``.

- **Debian** - Debian is the distribution from which Ubuntu is based, and is maintained entirely by open-source developers. There is no commercialized portion of the Debian project, unlike Ubuntu or RHEL.

- **Ubuntu** - Ubuntu is a Linux distro based on Debian, and maintained by Canonical. Ubuntu is like a slightly more mainstream version of Debian, and is maintained by Canonical, a commercial company. Ubuntu is free, but Canonical makes money by offering support services for Ubuntu and by including some bundled programs with Ubuntu (such as the Amazon integration in the Ubuntu Unity desktop environment).

- **DEBs [``.deb``, packages]** - These are package files meant to work with ``dpkg``. DEBs are like an offline version of APT. APT provides auto-updating functionality, DEBs are more like a traditional "install this once" installer. They only work on systems with ``dpkg`` installed though, such as Ubuntu or Debian.

- **``dpkg``** - Command line package installer to install ``.deb`` packages. You should only use ``.deb``s if there is not an APT option since ``.deb`` files are more hassle because of the lack of updating.

- **Aptitude** - text-based GUI for APT. Essentially a crude app store.

- **CURSES** - text-based GUI system. Google "curses gui" for screenshots and examples. Often used for programs too complex to be command-line-only, but that need to run without a desktop environment.

- **``/dev``** - Directory in Linux that represents all of the devices, including hard drives, optical drives, USB drives, microphones, video capture cards, webcams, etc. Basically anything connected to the PC is probably represented here. For example, ``/dev/sda`` is "SATA Disk A". ``/dev/cd0`` is the optical drive.

- **Mount** - System for accessing storage in Linux. Unlike Windows, Linux does not require drives to act separate. You mount a partition on a drive somewhere in the Linux filesystem and then you access the files on that storage. For example, I might have my root directory (``/``) mounted on a 100GB partition, ``/dev/sda1``. If I wanted all my home directories to be stored on a different partition, ``/dev/sda2`` for example, I could mount ``/dev/sda2`` at ``/home``. Now when I access ``/home`` I am using ``/dev/sda2``, but when I access somewhere else I am using ``/dev/sda1``. *This is very different from Windows, where you have to select the drive letter in order to access something!*