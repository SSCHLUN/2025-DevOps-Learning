# What I Learned

### Disk Partitions
- lsblk helps break down disks and their partitions 
- sudo fdisk - /dev/sda
	- This shows us a more detailed set of info based on the disk and its respective partitions.
-  3 Types of Partitions
	- Primary - Used to boot an OS
	- Extended - Cannot be used on their own but can create logical partitions.
	- Logical - Created within an extended and used for holding particular data
- MBR - Master Boot Record partition style.
	- Max Size of 2 TB
- GPT - GUID Partition Table
	- Theoretically an infinite number of partitions can be made
	- No max size
- if we want to create partitions out of an extended partition use > gdisk /device/path

### File Systems in Linux
- You cant just write data to partitions. File systems need to be created and then mounted to a directory.
- Various types of file systems ext2,3,4 
- mkfs.type(usually ext4) /device/path - Creates the File system
- mkdir /mnt/type; mount /dev/path /mnt/path - Creates a directory for mounting and then mounts.
- mount | grep /dev/path - Checks to see if our mount was successfully put in the right locations
- /etc/fstab is a file that lets is add these mounts so their are always available on restart
- echo "/dev/path /mnt/path type rwx(depends) 0(Backup Y/N 0(The pass lets us determin the order of these file systems activations and runs)) " >> /etc/fstab

### DAS NAS and SAN
- DAS - Directly attacked to a single host but gains high speed and low cost.
- NAS - The devices are not directly connected to any one host but rather another device on the network that hosts the disks and file systems. 
- SAN - Uses a LUN to provide access to the SAN as a disk. This allows for a high through put using its Fibre Channel Switch. Largest advantage is high functionality over a NAS for more critical applications and DBs.

### NFS File System
- Works on a server client model 
- Exports its mounted filesystem to other machines on a network.
- Doesn't take up their space but can be used like its a mounted disk on their own PC.
- Hosted on a NAS usually.
- hosts the exports for a particular directory in its /etc/exports file
- then it adds the IP addresses of the valid hosts in this file with the directory they should have access to.
- required specified ports to be open on both 
- exportfs -a exports to all devices and directories in the /etc/exports file
- exportfs -o IP address:/path/to/dir

### LVM (Logical Volume Manager)
- Allows multiple physical volumes to be bunched together then re distributed as logical volumes.
- Logical volumes can be dynamically resized as long as their is ample physical space.
- Requires some number of disks preferbaly unused
- lvm2 is a package that may not be on the system
- pvcreate lets us define a disk as a physical volume using > pvcreate  /dev/path
- vgcreate groupname /dev/path1 , path2, path3, etc. - Creates the group these phsyical volumes will occupy.
- pvdisplay lets us see the physical vumes available
- vgdisplay lets us see the group and its data avaibality and members.
- to create a logical volume we use
	- lvcreate -L(Linear) 1G(Size) -n(name) volume group
- lvdisplay will show us our logical volume.
- lvs - logical volumes list.
- vgs - lets us see if the group has enough space
- lvresize lets us update the size of a logical volume.
- resize2fs /dev/groupname/logical volume lets us update the file system to match the size of the logical volume we just updated.
- 




# What I Did

### Lab 1:

- Create a new GPT Partition on a pre-existing  disk
- Understand the navigation of the gdisk command and its arguments 

### Lab 2: 

- Checked to see which disks had file systems
- Checked for the file system type with sudo blkid /device/path
- Created a file system called data
- Mounted the file system to a disk with no file system in directory called /mnt/data
- Checked to see if the mount was successful using grep | /dev/vdb
- failed sudo echo command forced me to use sudo vim /etc/fstab
- manually added in the entry 
	- /dev/path /mnt/path ext4 rw 0 0 
- This made the file system persistent across reboots.
  
### Lab 3
- Verified the current logical volume I was working in - lvs
- Found un used disks on the device. - using lsblk
- turned them into physical volumes - using pvcreate /dev/name
- grouped the 2 new physical volumes into a group - using vgcreate /dev/name1 /dev/name2
- created a logical volume for this group called data - using lvcreate -L 1G -n data vgname
- created a mounting directory called /mnt/media
- used sudo mkfs.ext4 /dev/mapper/vgname-data to make a file system for this volume group
- used sudo mount /dev/mapper/vgname-data /mnt/media to mount the file system to media.
- resized the logical volume with an additional 500MB using lvresize and then specifying with -L +500M and then directed it towards the -n /dev/mapper/vgname-data 
- this then allows us to resize the file system so we can take advantage of this new space using a 
	- sudo resize2fs /dev/mapper/vgname-data we use the vgname becasue the file system is inherent to this logical volume so we dont need to specify it.
# Important Notes