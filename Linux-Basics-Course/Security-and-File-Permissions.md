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

* /etc/passwd is an access control file.
  - doesnt save the passwords but can set them.
  - Formatted like USERNAME:PASSWORD:UID:GID:GECOS:HOMEDIR:SHELL
* passwords are saved in /etc/shadow
  - Formatted like USERNAME:PASSWORD(HASHED):LASTCHANGE:MINAGE:MAXAGE:WARN:INACTIVE:EXPDATE
* groups can be seen in the /etc/groups
  - Formatted like NAME:PASSWORD:GID:MEMBERS

# User Management
* useradd name for sys admins to add users to a host.
  - takes a set of custom flags for configuration
    - -c for custom comments
    - -d custom home dir
    - -e for expiry date
    - -g for a specific GID
    - -G for multiple secondary groups
    - -s for a specific login shell
    - -u for a specific UID
* passwd name to set password 
* BOTH ADD AND PASSWD need to be ran as ROOT
* Once a user is logged in they can change their own passwd
* userdel name deletes users as root
* groupadd -g GID name_of_group
* groutdel  name_of_group

# File Permissions and Ownership

* broken into rwx rwx rwx
  - first 3 are the owner second the group third others
* permissions are established ona per file basis
  - r - read - 4 
  - w - write - 2
  - x - execute - 1
* these permissions are read sequentially so if you are the owner and dont have perms but are in a group that does have perms you wont be able to do what the owner can do despite being in a group with full perms.
* chmod works by adding and subtracting permissions from user, groups, and other.
* if we ran > chmod u+rwx,g+rw-,o-rwx we are efdfective saying add all to owner, add rw to group and remove all from anyone else.
* we can also run this in numerical notation > chmod 777 takes the octal value and applies it in the owner, group, other order. So a faster way to write the above command would be chmod 760 file.name
* chown changes the owner:group for a file.
* chown username file will maintain the group status while not changing the owner.
* chgrp group_name will change the primary group and leave the owner alone. 

# SSH and SCP

* ssh lets you connect remotely to a host.
* you can also pass a command like > ssh <user>@<hostname> to connect to that specific user account on that machine.
  - or use the -l flag before specifying the user with no '@' symbol.
* to do passwordless logins you can create keypairs.
  - users trying to ssh to the host need a private key
  - hosts need to have any publickeys installed that reference the users private key.
  - create keypairs by running > ssh-keygen -t(type) KEY_TYPE (RSA, ed25519, ecdsa, etc.)
  - to share we run > ssh-copy-id user@remote_host
* files holding public keys are saved in a hidden > /home/user/.ssh/authorized_keys where you will see this key saved.

* scp gives us a secure way to copy files over an ssh connection.
  - first verify ssh connectivity
  - then run > scp /path/to/file remotehost_name:/path/to/(file is specifed already so unless you want to change the name leave as blank.)
  - you need write permission in whateer dir you are trying to copy to ie copying to /root wont work
  - copying directories is as you would expect run > scp -p(maintain file perms)r(recursive) /path/to/dir/ remotehost_name:/pathto/dir

# IP Tables

### What I Did

# Lab 1 

* Created user account and password for a user
* added a group at a specific GID using groupadd -g 1010
* added a user with a specific login shell, user id and primary group using : useradd -u 1010 -g 1010 -s /bin/sh
* all ran as sudo

# Lab 2

* we inspect and change file permission using ocatal notation for efficieny
* found a user using grep -i username /ect/passwd
  - then we took the UID from that and ran > chown UID file.name
* after we found the parent directory and ran > sudo chown -R UID dirname/ to turn that directory and all files internally into files owned by the new owner.

# Lab 3 

* Verifies we know what port to have active for ssh its 22
* made public and private keypair using > ssh-keygen -t rsa
* sent the public key to the remote host using > ssh-copy-id user@remote_host
* verified we know to find keys in hidden file /home/bob/.ssh/authorized_keys
* used > scp /path/to/file.tar.gz remote_host:/path/to/ | to move data from one host to another

### Important Notes

SSH uses port 22
Private keys are held by users public keys held by host.
Use octal notation to change filer permissions
-t flag in key-gen is for the encryption method
-pr in scp is for perserving file perms and running recursively through directories.
