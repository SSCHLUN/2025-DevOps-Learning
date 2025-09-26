### What I Learned

# Linux Accounts

* information on user accounts is saved in /etc/passwd
  - has a username
  - UID
  - GID
  - information on the home directory
  - also saves information the default shell
* information on groups is saved in /etc/group
* super user account has the UID 0
* system accounts for software have UID < 100 or between 500-1000
* service accounts for services have UIDs aswell.
* id command gives info on an individual user.
* to see currently logged in users.
* last lets us see the history of user logons.

* Sudo is a super user we can swap too as needed.
* we can look in /etc/sodoers to look at the permission with sudo for individual users and groups
* in the /etc/sudoers file we can look at some syntax structure
  - in the file we see seperations between users and groups denoted by a %
  - given the line user ALL=(ALL:ALL) ALL each tag means something
    - first text is the user being configured
    - the next next is the hosts either localhost,specific remote host,ALL for anyhost.
    - then it allows us to define a range of users:groups who we can run mannds as ALL:ALL applies to everyone and group.
    - the final text allows us to define what commands can be run as a super user.
    - ie sam1 localhost=/usr/bin/shutdown -r now. Would allow me to only run commands as myself and the specific command that I am running is to shutdown. we dont specify the users and groups just who is doing what on which host.
   
# Access Control Files

* 

### What I Did



### Important Notes
