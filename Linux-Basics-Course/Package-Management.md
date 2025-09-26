### What I Learned

* Packages are compressed files containing all the data required for some software to run.
* Package managers are what manage and control the removal and update process of any gtiven package on a linux machine.
  - Manage check sums and suthenticity
  - Simplify the process to find and download old and new packages
  - Manage the depndencies
* Distros are seperated by their package managers.
  - .RPM covers things like RHEL and CentOS
  - .DEB covers things like Debian, Ubuntu, and Mint
* DPKG, APT, APT Get
* RPM, YUM, DNF as you move right it gets front end develoipment and feature richness.
* RPM or Red Hat Package Manager
* .rpm ius the file extension
* 5 Core Functions of RPM
  - Install
  - Uninstall
  - Upgrade
  - Query
  - Verify
* rpm -ivh file.extentsion to install with all the deatils being shown on screen
* rpm -e file.extension to uninstall
* rpm -Uvh to upgrade
* rpm -q to look at file deatils
* rpm -V to validate the data has been installed from a secure place.

* yum package managers works on top of rpm
* Works with software repos to manage dependencies.
* Automatic Dependencies management.
* yum repolist lists the repos we have installed.
* yum provides commandname to find what repo provides a command
* yum remove packagename
* yum update package to handle single instance updates.
* yum update with no pointer just upodates everything managed by yum

---

* dpkg can be used for similar functions to rpm
  - Install use dpkg -i 
  - Uninstall use -r
  - List use -l
  - Status use -s 
  - Verify use -p 
* apt/apt-get is the dependency manager
* apt works better generally.
* also works on software repo
* apt update - download packages from anywhere
* apt upgrade - installs the downloads to their resp[ective locations
* apt edit-sources - allows you to use a text editor to configure pacakges manually
* apt install - installs
* apt remove - removes packages
* apt search - lets us look for a package in a specific repository
* apt list | grep package to look for a package in all repos.


### What I Did

# Lab 1

* used ssh to conenct to another host running CentOS
* rpm -q to get specific package details like version.
* ran yum install firefox to get the files from a server when they doulndt be found in the downloads using rpm
* yum repolist to see the various software repos we have installed.
* yum proivides will show the exact package repo in the form of a long link.

# Lab 2

*basically lab 1 but for apt and dpkg I prefer apt over yum.

### Important Notes

Theres alot of package managers they all seem to basically do the same thing with varied levels and features. Be specific in file names and run anything that adds or removes files from the whole system as a super user.
