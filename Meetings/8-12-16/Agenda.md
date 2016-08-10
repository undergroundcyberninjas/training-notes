# BHS CyberNinjas Initial Meeting
## On 8-12-16

**Objectives:**

- Take attendance and split up into teams
- Review with Kahoot
  - PC Parts Review
  - Linux Permissions Review
  - Linux Package Management Review (optional)
- Assign Numbers
  - Depending on the number of teams, give each team a VM or give each member a VM. 10 containers maximum due to RAM constraints.
- Give everyone assignment (tbd) on Linux VMs

### Linux Practice Assignment #1
- Create a new user called ``captainsparrow`` with password ``why1stherumg0ne?`` for 5pts
- Create a new group called ``pirates`` and add ``captainsparrow`` to it for  10pts
- In ``captainsparrow``'s home directory, create a directory called ``tools`` for 2pts
- Inside ``/home/cyberninja/tools``, use ``wget`` to download the file at the URL below (for 15pts):
  - ``http://hm.evilgeniustech.com/cyberpatriot/labs/8-12-16/doAnInternet.sh" 
- Set the group for ``/home/cyberninja/tools/doAnInternet.sh`` to ``pirates`` for 15pts
- Add ``cyberninja`` to the group ``pirates`` for 10pts
- Give the group ``pirates`` permission to read and execute, but NOT write, to ``doAnInternet.sh``. Make sure ``cyberninja`` still has permission to read/write/execute. For 20pts
- Call over a teacher and run the script ``doAnInternet.sh`` by changing to the ``/home/cyberninja/tools/`` directory and using ``sh the-path-to-the-script``, inserting the actual path to ``doAnInternet.sh``. The teacher will tell you whether you've done everything correctly based on the script's output. For 100pts

The highest possible number of points is 177.
