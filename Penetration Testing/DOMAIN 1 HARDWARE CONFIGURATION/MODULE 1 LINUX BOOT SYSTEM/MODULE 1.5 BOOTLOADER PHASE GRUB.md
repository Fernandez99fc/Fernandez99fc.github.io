OBJECTIVES: 
EXPLAIN HOW THE GRUB or GRand Unified Bootloader WORKS. 

GRUB is the legacy bootloader use to bring up the Linux OS. The purpose of GRUB and other bootloaders is to bring up the linux system kernel. GRUB uses the initrd(Initialize Ram Disk)to bring the OS into memory
The Boot directory contains:
INITRD
Linux Kernel:
Linux(Uncompressed Format)
Linuz(Compressed Format)
And other files required to boot

/Boot contains files that aren’t used by the operating system but by its bootloader. You’ll find files of the bootloader itself like(/boot/grub/*for GRUB) and the Linux kernel(/boot/linux or /boot/linuz also the INITRD.

The boot manager is located at the EFI\MICROSOFT\BOOT\ sub folder of the EFI system Partition 

Bootloader can be stored in two places. The first block of the medium and the other is the specific partition on the medium 

The GRUB menu is configured in of these files:
grub.conf:/boot/grub/grub.conf
menu.lst:/boot/grub/menu.lst 

The default configuration file is:
/boot/grub/menu.lst

And other files required to boot linux

GRUB Operates in stages. The stages are: 
Stage 1>Stage 1.5 and Stage 2. 
Stage 1 is where the MBR finds GRUB and points down to stage 1.5 or stage 2 


