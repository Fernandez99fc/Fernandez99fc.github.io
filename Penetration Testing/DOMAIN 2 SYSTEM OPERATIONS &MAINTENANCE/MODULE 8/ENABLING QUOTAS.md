OBJECTIVES-----------------------------
Understand the process of enbling quotas in linux....
working with the quotacheck command

 Disk quota is a utility or tool used by system administrators to restrict certain aspects of the file system usage or in other to manage the file system in a better way.  It restricts users to create files or limit the file system users.
 
To enable quotas on linux requires a number of steps.  Because we are modyfying  a file system, we have to specify mount options, which involves /etc/fstab. To enable quotas, we have to modify the /etc/fstab.

lsblk -provides useful information on block devices.
block devices are devices that are written to and read a block at a time(512 bytes)

lsblk displays:
name of the block device,block device partitions,sr0.
RM-removable
MAJ:MIN- MAJOR AND MINOR NUMBERS.
RO- Read only
SIZE of block device
TYPE- type of block device, is it a disk,partition,cd rom
MOUNT POINT

NOT DONE------------- 