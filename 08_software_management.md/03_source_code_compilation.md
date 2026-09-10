# Compiling software
Typically some software needs to be compiled manually. There are several reasons including,
* Security patch
* Installing latest version
* Package not lsited in package managers
* installing different versions

Most of the software needs to be compiled using c or c++ compilers gcc and g++ respectively. To compile the packages, the compilers needs to be installed first. This can be done by:

- `sudo apt install build-essentials` In ubuntu. before installing, updating the apt repository is recommended. is required
- `sudo dnf group install "Development Tools"` In CentOS or related distros like AlmaLinux or RHEL. 

These will install plenty of things including gcc, g++ and make. The make is an utility to build a collection of source files and transform them into the final product.

Compiling means converting human readable codes to machine readable codes. The compilers does that job.


## Advantage and disadvantage
THe source compilation have some advantages and disadvantages which are,
- **Advantages:**
    1. can be compiled with certain options which may be missing or disabled in the standard distribution package. For example IPv6 enabled.

    2. Access to the latest version of an application

    3. Its possible to have multiple versions of the same program installed.

- **Disadvantages:** 
    1. The package manager will be completely unaware of the changes done by the user.

    2. If not careful when compiling to install the program in separate location can berak the system

    3. Its not easy.


