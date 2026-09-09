# APT
APT stands for Advanced Package Tool. The apt-get and apt-cache is merged into the single command `apt`. The recommended way to manage software packages on ubuntu and other debian distro is using apt.

An apt repository is a web server which contains a collection of packages with metadata that is readable by the apt tool.

> To manage apt packages internet connection is required.

APT can be used to install, update, and remove packages from the systems. Repositories are essential for storing, managing, and deliverying software. A special kind of repository hosted on servers like Launchpad are PPAs(Personal package archives)

APT use an index or a local database that holds records of available packages from the repositories enabled in the system. To update the pacakge index `sudo apt update` command can be used. This will pull the latest records.

> When installing or upgrading a package, updating the records on apt is recommended.

### Installing an apt package
To install an apt package, basic command `sudo apt install [package name]`. Example command: ` sudo apt install apache2`.

> If the package alredy installed then apt istall will upgrade the package to latest version

To install multiple packages at once, the package names should be passed as space separated arguments. Example command: `apt install vlc code chrome`. 


APT can also install downloaded deb file just by running `apt install [absolute file path]`.If full path is not provided then it will give an error `unable to locate package` Behind the scene the apt will call the dpkg package manager to install this package.

### Upgrading packages

To find the list of upgradeable package `apt list --upgradable` command can be used.

To upgrade the full system `sudo apt full-upgrade` command is used. `-y` option can be used to confirm the installation non interactively. 

### Removing packages
To remove a package simple command `apt remove [package name]`. And to remove multiple package, the package names have to be passed as argument in space separated format. Apt remove will leave some configuration file behind. 

To remove all configuration file `purge` option is used. Example command: `sudo apt purge apache2`. But None of them removes the dependencies. 

To remove the dependencies `sudo apt autoremove` command is used.

By default, ubuntu keeps cache of all installed and upgraded packages. To clear the local repository cache `sudo apt clean` command is used. This will only keep the lock file and remove everything.

## Information and searching of packages

To list all the available packages, apt command is run with the option `list`. Command: `sudo apt list`. To search for a specific package, grep command can be used with pipe. 
To get list of all installed packages, `--installed` option have to be added.

To find packages by a phrase on a package description, search option with apt command can be used. Example command: `sudo apt search "mail server"`. 

To find information about a package, `apt show [package name]` command is used.

There are also available GUI package manager called `synaptic`. This gives the user a graphical user interface who can do all things like apt.