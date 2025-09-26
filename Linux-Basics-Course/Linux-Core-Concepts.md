# Linux Core Concepts Module

### What I Learned

* uname -r provides the name of out specific linux kernel.
  - It takes the form [KernelVesion.MajorVer.MinorVer.PatchRel]
* Kernel Space vs User Space
  - Kernel
  - Device Drivers
    - Kernel Code
    - Kernel Extensions
    - Device Drivers

  - Applications and Programs
    - Functions ran in Languiages like C, Java, Python, Ruby
    - Also houses things like docker containers

  - System Calls allow for applications and programs to ask the kernel and related drivers to be able to do things like allocate memory or to get a file if needed.
    
* When pluggin in hardware to a Linux system a logical path is followed.
  - The USB gets plugged in -> a device driver is associated with that device -> uevent occurs and sends data to user space area called udev where there will be a /dev/[device identifier]
* dmesg lets us see how devices are interactin on our machine.
  - we can grep this with dmesg | grep -i [device]
* lspci lets us see info about all pci devices
* udevadm monitor prints out recieved events for udev abd the kernel events.
* lsblk shows us block devices
  -sda's are the partitions on these block devices.
  -uses the format MAJ:MIN to refer to various major device codes and their subsequent parts that also reference the same major code
    -Major 1 Ram
    -Major 3 HD or CD ROM
    -Major 6 Parallel Printers
    -Major 8 SCSI Disk
* lscpu lists cpu details
* lshw lists details around device configuration
  - ran with sudo
* Linux Boot Sequence | POST -> Boot Loader(GRUB2) -> Kernel Init -> INIT Procoess (SystemD)
* RunLevels are a way to determine which interfacing method you are using when interacting with your Linux kernel
  - Level 5 is GUI - SystemD = graphical.target
  - Level 3 is CLI - SystemD = multiuser.target
  - Level 0 is poweroff.target
  - Level 1 is rescu.target
  - Level 2 is multi-user.target
  - Level 4 is multi-user.target
  - Level 6 is reboot.target
* systemctl get-default prints out the systemd default target
* running a ls -ltr /etc/systemd/system/default.target
* systemctl set-default multi-user.taget lets us specify which run level we want to boot into during the linux kernel boot sequence.
* Regular Files are as we kind of expect for normal user use.
* Directoies are files that hold other files in an organizational box.
* Special Files are as listed
  - Character Files - These are the devices attached to external ports.
  - Block Files - represent block deviceds
  - Links | Hard Links - associates two or more links that refer to a specific set of data on a block. Softlinks are pointers to another file like shortcuts
  - Sockets allow for communication between two seperate processes.
  - Named pipes connect one process an input into another one allowing for relative changes in a processes output.
* file command is another way to look at file types more directly.
* while ls -l... can show us a variety of file types when lookling at the file permisions.
  - d is directory
  - '-' is a regular file
  - c is a character device
  - l is a link
  - s is a socket
  - p is a pipe
  - b is a block device

### What I Did

### Lab 1

* run simple kernel information commands like lsblk and dmesg 
* answer questions in regards to the Kernel Version and Major Versions to show we can identify these things.

###Lab 2

* make use of the sudo command to run file commands on /root/files.
* Block devicces being found from lsblk can be found in the /dev file.
* Used sudo lshw to find specific information about a ethernet ports vendor.

### Important Notes

/opt directory is the standard spoace to install any third party applications.
/mnt is used to mount files systems temporarily.
/tmp is to store temporary data.

