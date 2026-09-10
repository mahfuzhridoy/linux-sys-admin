# DPKG
dpkg ins used for installing `.deb` package. This is used by all debian based distros. This is an archive that contains other files including executable application that was already compiled. 

dpkg can be used to install downloaded files. DPKG provides the ow level infrastructure for package management. The dpkg database contains the list of the installed software in the current system. It can work with local deb package files and does not work know about repositories and does not solve dependencies like apt does. The apt behind the scene calls dpkg.

## Installing files
dpkg can install downloaded local packages with command `sudo dpkg -i [package name]`. To get information about the packages, `--info [package name]` option is used.

To installed more packages than one, the package names have to be passed as arguments separated by white space. Example command: `sudo dpkg -i chrome.deb firefor.bed`. This is useful when installing multiple packages which are circularly dependent on each other.


## Removing files
To remove an already installed package, `-r` option of dpkg is used. Example command: `sudo dpkg -r google-chrome-stable`. The `-r` does not remove the configuration files. If the package is reinstalled, then the configuration will be same if not removed previous ones.

To remove a package along with its configuration file `-P` option is used. The P works like purge option of apt command. 

## Files info
To get list of all installed files, `dpkg --get-selections` command is used. And to see the package version, architecture and short descriptions  `dpkg-query -l` and can be filtered with `grep`. The first two letter indicates the desired state and curent state respectively.

The debian package is an archive that contains other files. To list all files installed on the system by a package, `-L` option is used. Example command: `dpkg -L [package name]`. And he package name can be found using the dpkg-query.

To see what package a specific file belongs to, `-S` option is used with the `dpkg` command. Example command: `dpkg -S /bin/ls`. this command will show the package name which ls belongs to. This is helpful when a file gets corrupted and need to reinstall the package.


