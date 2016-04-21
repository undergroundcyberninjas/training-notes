# Linux Permissions Notes

[**This lecture is built around a tutorial video, located here.**](https://www.youtube.com/watch?v=vKTg1ATHl4E)

---

## Permissions Concepts

When you assign permissions, you're assigning them to one of three units.

- **User** (represented by ``u``)
- **Group** (represented by ``g``)
- **Other** (represented by ``o``, also sometimes called "World" or "Everyone")

*Remember, a Group on Linux is just a collection of Users.*

There are three different permissions available:

- **Read** (represented by ``r``) : Ability to view the contents of a file or directory
- **Write** (represented by ``w``) : Ability to change/delete/rename a file or directory
- **Execute** (represented by ``x``) : Ability to run the file as a program

---

## Reading Permissions

We can read permissions using the ``ls -all`` command. Let's take a look at the output of the LS command.

```
cyberpatriot@demo-1:~$ ls -ll
total 29
-rw-r--r--  1 cyberpatriot cyberpatriot 16636 Apr 12  2014 cmatrix_1.2a-5_amd64.deb
-rw-r--r--  1 cyberpatriot cyberpatriot    64 Apr 15 16:29 hamburger
drwxr-xr-x+ 2 cyberpatriot cyberpatriot     4 Apr 14 16:42 myscripts
drwxr-xr-x+ 2 cyberpatriot cyberpatriot     3 Mar 29 14:20 mytextfiles
```

The column to the far left represents the permissions. It uses letters (``r``, ``w``, and ``x``, or ``-``) to represent the different permission types. The two columns that read ``cyberpatriot`` represent the user and the group. The left one is the user, the right one is the group. (It just so happens there's a group *and* a user with the same name)

The letters are in groups of 3, representing the ``user``, ``group``, and ``other`` permissions, respectively. Again, ``r`` means read, ``w`` means write, ``x`` means execute, and ``-`` is a placeholder when a permission is disabled. The first character, which is either ``d`` or ``-``, shows whether it's a file or a directory, so ignore that for now.

Looking at the permissions for the file ``hamburger``, we can see it says ``rw-r--r--``. Remember, the permissions are grouped in sets of 3 letters for each permissions unit. So ``hamburger`` has read/write permissions for the user, read-only permissions for the group, and read-only permissions for the rest of the world.

Another example is the directory, ``myscripts``. Its permissions read ``rwxr-xr-x``. This means the user can read, write, and execute; the group can read and execute; and "other" (aka everyone else) can read and execute.

---

## Editing Permissions

To change permissions on Linux, we use the ``chmod`` command. Using the letters that represent permissions units and permissions themselves, we can add and remove permissions. For example, ``u+x`` means ADD the EXECUTE permission to the USER. The minus sign (``-``) takes away permissions, so ``g-w`` would REMOVE the WRITE permission from the GROUP.

Now take that knowledge, and combine it with the chmod command and a file path. So to give the user read/write permission for ``./file1``, I would run ``chmod u+rw ./file1``.

#### Examples:

- ``chmod g-x ./file1`` : remove the execute permission from the group for ``./file1``
- ``chmod o+rx ./file1`` : give "other" read/execute permission for ``./file1``
- ``chmod go+r ./file1`` : give both the group and "other" read permission for ``./file1``

### Number Method

``chmod`` also supports using special combinations of numbers for super-fast permissions changing. Instead of having 3 characters for each permissions entity, you have only one number, which is the sum of all your permissions.

#### Octal Permissions:

- Read : ``4``
- Write : ``2``
- Execute : ``1``
- No Access : ``0``

Simply add these together to get the "magic numbers" for your permissions. So for example, if you wanted read/write permissions, ``4 + 2 = 6``, so you'd use ``6``. If you wanted read and execute, but no write, ``4 + 1 = 5``.

#### Examples:

- ``chmod 000 ./file1`` : Give user, group, and other no access
- ``chmod 755 ./file1`` : Give user read/write/execute; give group and other read/execute
- ``chmod 644 ./file1`` : Give user read/write; give group and other read
- ``chmod 777 ./file1`` : Give user, group, and other read/write/execute

---

## Setting Users/Groups

Now we know how to give permissions to the user and the group owner of a file. But how can we tell Linux *which* user and group that is for a specific file?

### ``chown``

You set the user, aka the owner, with the ``chown`` command. It also has the option of setting the group as well. Its syntax is very simple. In the example below, I am setting the owner (the user) of ``./file1`` to ``tomhanks``.

``chown tomhanks ./file1``

You can also specify a group with a colon and a group name. For example:

``chown tomhanks:oscarwinners ./file1``

This means the owner of ``file1`` is ``tomhanks`` and the group owner is ``oscarwinners``. So that's who we're actually assigning the user/group permissions to.

### ``chgrp``

You can also change only the group with ``chgrp``.

``chgrp oscarwinners ./file1``
