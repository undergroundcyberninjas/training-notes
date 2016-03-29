# Package Manager Cheat Sheet
#### For Ubuntu/Debian

Here are are some of the most common APT tasks (``<package-name>`` represents a package name _without_ the ``<>``):

| Task                                          	| Command                                   	| Description                                                                                                                                                                                                       	|
|-----------------------------------------------	|-------------------------------------------	|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| **Upgrade**                                       	| ``apt-get upgrade``                       	| Updates the _actual packages_, but should usually be run _after_ ``apt-get update``.                                                                                                                              	|
| **Update**                                        	| ``apt-get update``                        	| Updates _information_ about packages, not the actual packages.                                                                                                                                                    	|
| **Fix Missing Dependencies**                      	| ``apt-get install -f``                   	| Checks to see if you have any dependencies missing and fixes them. Useful if APT crashed or was killed unexpectedly during a package install. Also useful when you've installed a ``.deb`` that has dependencies. 	|
| **Install**                                       	| ``apt-get install <package-name>``        	| Installs package named ``<package-name>``                                                                                                                                                                         	|
| **Uninstall and Purge**                           	| ``apt-get remove --purge <package-name>`` 	| Uninstalls ``<package-name>`` and deletes any cached package files from your computer. _Does not remove dependencies!_                                                                                            	|
| **Automatically Remove Unnecessary Dependencies** 	| ``apt-get autoremove --purge``            	| Removes any dependencies and deletes and cached package files from your computer.                                                                                                                                 	|
| **Setup Again**                                   	| ``dpkg-reconfigure <package-name>``       	| Goes through the package's initial setup again. Useful if you accidentally put in something wrong when you set it up, or if you broke a configuration really badly and need to start over.                        	|
| **Install from .deb**                             	| ``dpkg -i /path/to/file.deb``             	| Installs ``/path/to/file.deb`` to your system. Does _not_ automatically fetch dependencies like APT, so you'll need to run ``apt-get install -f`` to fix that.                                                    	|