# Basic Linux Commands That We Haven't Covered

## ``wget``

Fetches files via HTTP, FTP, etc. This is often used on servers to download package files/scripts from the internet.

###For example:

We know the URL of the package file we want: ``http://ftp.us.debian.org/debian/pool/main/c/cmatrix/cmatrix_1.2a-5_amd64.deb``

So to download it on the server, we run ``wget http://ftp.us.debian.org/debian/pool/main/c/cmatrix/cmatrix_1.2a-5_amd64.deb``

Now we can use that file.

## ``top`` and ``htop``

These commands show you CPU/RAM usage as well as what processes are running on your system. ``htop`` is just a more user-friendly version of ``top``, but ``htop`` usually doesn't come preinstalled, while ``top`` does.

## ``shutdown`` and ``reboot``

Both these are pretty self-explanatory. ``shutdown`` requires some parameters to totally halt your system:

``shutdown -h time``

- ``-h`` means "halt the system"
- ``time`` is usually ``now`` but can also be a scheduled time

``reboot`` doesn't require parameters to work.

Both ``shutdown`` and ``reboot`` require root priveleges, so you'll need to prefix them with ``sudo``.
