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



### What I Did

### Important Notes
