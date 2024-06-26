OBJECTIVES
---
EXPLAIN BLOCK STORAGE.
USE THE LSBLK AND BLKID COMMANDS.
LEVERAGE THE /SYS/BLOCK DIRECTORY...

BLOCK DEVICES
--
BLOCK DEVICES STORES DATA IN FIXED-SIZE BLOCKS, GENERALLY:
512 BYTES
1 KILOBYTE
2 KILOBYTE

A BLOCK IS THE SMALLEST LOGICAL UNIT OF ADDRESSING THE LINUX KERNEL RECOGNIZES.
SO..HOW DO WE IDENTIFY BLOCK DEVICES?

LSBLK
--
THE LSBLK COMMAND IS USED TO LIST BLOCK DEVICES.
LSBLK -p- PRINTS THE FULL PATH FOR THE BLOCK DEVICES...
LSBLK -fs DISPLAYS FILESYSTEM FOR THE DISK DEVICES..

BLKID
--
THE BLKID COMMAND IS USED TO GET MORE INFORMATION ABOUT BLOCK DEVICES AND THEIR PARTITIONS ALSO UUID...
BLKID - DISPLAYS THE INFORMATION..
LS /VAR/DISK/BY-UUID- POINTS OUT THE UUID OF BLOCK DEVICES

/SYS/BLOCK
--
THE KERNEL USES THE INFORMATION IN THESE DIRECTORY TO INTERACT WITH THE DEVICES.