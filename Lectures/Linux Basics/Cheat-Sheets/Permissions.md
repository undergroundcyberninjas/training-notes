# Linux Permissions Cheat Sheet

### Units:

- User (``u``)
- Group (``g``)
- World/Other (``o``)

### Permissions

| **Permission** | **Letter** | **Number** | **Description**                                                  |
|----------------|------------|------------|------------------------------------------------------------------|
| Read           | ``r``      | ``4``      | Read the contents of a file, or list the contents of a directory |
| Write          | ``w``      | ``2``      | Change/delete a file, or change/delete a directory               |
| Execute        | ``x``      | ``1``      | Run the file as a program                                        |

---

### ``chmod``

**Letter Method:**

```chmod [-R] [u|g|o][+-][r|w|x] /path/to/file```

**Number Method:**

Add the numbers from the table to get the permissions number you need. For example, ``rwx`` is ``7`` because ``4 + 2 + 1 = 7``

```chmod [-R] 777 /path/to/file```

*The ``-R`` option on both methods uses recursion*

---

## Ownership

### ``chown``

```
chown USER:GROUP /path/to/file
```

The ``:GROUP`` is optional.

### ``chgrp``

```
chgrp GROUP /path/to/file
```

Changes only the group owner. Can be used in place of ``chmod`` with group argument.
