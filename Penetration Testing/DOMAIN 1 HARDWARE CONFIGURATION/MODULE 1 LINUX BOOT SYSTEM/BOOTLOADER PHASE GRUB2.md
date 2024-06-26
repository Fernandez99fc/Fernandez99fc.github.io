
OBJECTIVES—————————
Explain how the GRUB2 Bootloader works

GRUB2 is the Grand Unified Bootloader 2 replacement for GRUB. Any version newer than 1.98 is considered GRUB2.

To check the version of GRUB you’re using:
grub-install -V(Debian based)
grub2-install-V(RPM 

GRUB2 Settings are configured in two places:
/etc/default/grub-Controls configuration variable. For instance,GRUB timeout,how long should GRUB stay up on the screen for.

/etc/grub.d- Contains Scripts that build the GRUB boot menu,the command lines that you see

You can create a custom script in /etc/grub.d. 
Once a user makes changes to GRUB2,you must execute the command grub2-mkconfig