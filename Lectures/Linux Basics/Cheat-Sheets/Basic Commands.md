# Command Line Cheat Sheet

Based on the Codecademy "Learn the Command Line" curriculum.

### Basic Filesystem Navigation
- ``pwd`` outputs the name of the current working directory.
- ``ls`` lists all files and directories in the working directory.
  - ``-a`` lists all contents, including hidden files and directories
  - ``-l`` lists all contents of a directory in long format
  - ``-t`` order files and directories by the time they were last modified.
- ``cd`` switches you into the directory you specify.
- ``mkdir`` creates a new directory in the working directory.
- ``touch`` creates a new file inside the working directory.
- ``sudo somecommand`` runs ``somecommand`` as root.
- ``lsblk`` lists all your hard drives and their mount points.
- ``ifconfig`` tells network interface configuration.
- ``sudo shutdown -h now`` powers off the machine.
- ``sudo reboot`` reboots the machine.
- ``netstat -tulpn`` shows any processes communicating on the network, and their ports
- ``htop`` shows all running processes.
- ``ufw`` is the command for Ubuntu's universal firewall. ``ufw enable`` turns on the firewall, ``ufw disable`` turns off the firewall.

