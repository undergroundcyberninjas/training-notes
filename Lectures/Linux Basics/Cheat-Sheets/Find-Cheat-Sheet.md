# Linux ``find`` Command Cheat Sheet

The ``find`` command can be used to search for files on the Linux filesystem. This is useful, for example, when the README says to find all MP3 files.

### Basic Syntax:

**``find location comparison-criteria search-term``**

- **``location``** : The place on the filesystem to search. To search the entire filesystem, use ``/``. Common parameters include:
    - ``/`` : The top of the file tree, so the entire filesystem.
    - ``/home/someuser`` : Search one person's home directory
- **``comparison-criteria``** : The properties you want to look at when searching. Common parameters include:
    - ``name`` : Search by name, is case sensitive
    - ``iname`` : Search by name, not case sensitive
- **``search-term``** : The value that goes with ``comparison-criteria``.
    - ``*.mp3`` : Search for all files that end in ``.mp3`` (all mp3 files).
    - ``something.*`` : Search for files called ``something``, with any file extension.
    - Remember that ``*`` (the wildcard) means "anything". So ``*.txt`` tells the computer "all files that end in ``.txt``", which is all text files. This is very useful during competition.

### Examples:

- **``find /home/cyberpatriot -name "somefile.txt"``**
  - Searches for ``somefile.txt`` inside ``/home/cyberpatriot``.

- **``sudo find / -name "movietrailer.mp4"``**
  - Searches the entire filesystem for ``movietrailer.mp4``.
  
### Common Mistakes:

- If you get ``permission denied`` errors, try prefixing your command with ``sudo``. You'll have to do this when you're searching files that don't belong to you.
- If you don't need case sensitive name searching, make sure to use ``-iname`` instead of ``-name``!
