## Linux Basics Lesson - Homework

---

1. Set up an Ubuntu Server 14.04 virtual machine. _(Extra Credit: Do not use the VMware "Easy Install" feature, do it the old-fashioned way with the traditional Ubuntu installer. You get bonus points and braggin' rights if you do this.)_
2. Make a user named after your team. Set their password to ``buckhorncyberninjas2016`` .
3. In the user's home directory, make a folder called ``cyberpatriot``. Create a text file called ``homework.sh`` inside the folder. Set that file where the owner can read/write/execute, the group can read/write/execute, and the world (other) can read.
4. Using a text editor (like ``nano``), put the following code in the ``homework.sh`` file:
```
#!/bin/bash
echo "Yes, I did the homework!"
echo "------------------------"
echo "Blast-off in 5..."
sleep 1
echo "4..."
sleep 1
echo "3..."
sleep 1
echo "2..."
sleep 1
echo "1..."
sleep 1
cowsay "INITIATING LAUNCH"
sleep 3
cmatrix
```

5. Install the package ``cmatrix`` and the package ``cowsay`` on your virtual machine and make sure all your packages are up to date.

6. At the next meeting, have this virtual machine ready to use on your computer.

---

**Email me (Hampton) if you have questions, need help, or you've figured out something cool. My email is ``k4kfh.radio@gmail.com``.**