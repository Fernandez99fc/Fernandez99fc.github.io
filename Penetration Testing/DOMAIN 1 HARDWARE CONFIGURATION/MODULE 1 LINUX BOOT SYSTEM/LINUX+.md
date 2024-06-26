APT AND YUM ARE PACKAGE MANAGERS IN LINUX 
APT(Advanced package tool) OR APT-GET is what is used when we work with debian or debain based distributions. YUM(Yellowdog updater modifier) is what is used when we work with Cent-OS or RPM(Redhat package manager) based distributions 

A Package Manager is a tool that allows users to install,remove,configure and update programs in an operating system 

The 3 Linux Distributions are Debian,Red hat and SUSE(SOFTWARE AND SYSTEM DEVELOPMENT COMPANY). All other distributions are based under these 3. 

Virtual file systems or pseudo file systems are /sys,/dev/proc 
Note: Linux boot process is a frequent topic in linux system admin interviews 

MODULE 1----- 
MODULE 1.1: THE LINUX BOOT PROCESS: 
The Linux boot process consists of 4 distinct phases: 
1)The bootstrap phase 
2)The bootloader phase(The grub boot loader menu) 
3)The kernel Phase(The kernel messages being ouputed in console during the boot process) 
4)The initialization phase 
Note:Bootloader is a program responsible for booting a computer 
MODULE 1.3 THE BOOSTRAP PROCESS: 
The boostrap phase is the first stage in the linux boot process. It is responsible for testing and bringing up the hardware so that the Operating system can be started. It finds the location of the bootloader which is necessary to move into phase 2. 

WE WILL COVER 3 BOOTSTRAP OPTIONS IN THIS LESSON: 
THE BIOS 
The UEFI/EFI 
The PXA 

Note:The BIOS is a ROM chip on the motherboard 
BIOS-Basic Input and Output system is the legacy boostrap program. BIOS looks through a list of devices in order (like Hard drive,usb,cd/dvd) to see if it can find the bootloader code or program. What BIOS is actually looking for is the MBR(MASTER BOOT RECORD) that contains the bootloader code we will use to move to phase 2 of the boot process. The bootloader helps to load the operating system into memory. Without the bootloader,the operating system wont be loaded into memory. 
 
BIOS checks all the hardware components in the computer to make sure that they’re there,up and running without any issue and they have access to the driver programs that they will need to run,that is what we call the power on self test(POST).This process is before looking through a list of devices for boot loader.

The MBR is stored in the first sector of a hard drive
Legacy boot is the boot process used by BIOS(The deprecated process) 

BIOS WAS DEPRECATED:----- 
It cant boot up drives largerthan 2.1TB. The reason is, the system that BIOS uses to access storage devices like Hard drive,SSD which is the MBR can only handle partitions less than 21TB 
limited to 16 bits addressing 
could only access 1mb of RAM
could only manage a limited number of devices 
Limited to 4 partitions

Note:The MBR uses maximum of four partitions,3 primary partitions which contains the os and can be bootable and an extended partition which contains logical partitions which can’t be bootable but only stored files

GPT Is a Modern partition table which can handle drives above 2.1TB and can allow you to extend your storage as much as you you you can unlike MBR…GPT comes with UEFI boot mode while MBR comes with BIOS.

UEFI/EFI- Unified Extensible Firmware Interface. It is the replacment for BIOS. 
It can boot drives of 2.1TB or larger 
It can operate in 32bit or 64bit mode with access to all devices and memory
It is configured in Linux with efibootmgr 

UEFI looks for storage device with an EFI system partition(ESP). ESP is Fat32 formatted and can be found in /boot/efi. 
Once the ESP has been found ,it then loads the files stored in the ESP partition on the hard disk to start installed OS or load a bootloader like GRUB 

BIOS Doesn’t know where the boot loader is,then it searches all devices while UEFI locates devices having the ESP for bootable media 

Thea ESP is a Partition in a hard drive or SSD containing the kernel image or boot loader of all operating systems. Once the computer boots up,the UEFI loads the files stored in the ESP to start installed operating systems.

GPT AND MBR ARE PARTITION SCHEMAS AND ESP MSR(is not MBR) ARE PARTITION NAMES

UEFI is the modern boot process 

PREBOOT EXECUTION ENVIRONMENT(PXE) 
It is used to boot a server remotely 

TWO REQUIREMENTS FOR PXE BOOTING: 
The system has to have a NIC that supports PXE 
The system has to have PXE enabled as a boot device 

When the system is turned on,the NIC tries to generate an Ip address,then the Trivial file transfer protocol(TFTP) is used to transfer files to the system. The system downloads the appropriate boot image from the TFTP Server's pxelinux.cfg directory 

MODULE OBJECTIVE: 
WE COVERED THE FIRST PHASE OF THE BOOT PROCESS-THE BOOSTRAP PHASE 
BIOS AND LEGACY BOOTSTRAP PROCESS 
UEFI AND MODERN BOOTSTRAP PROCESS