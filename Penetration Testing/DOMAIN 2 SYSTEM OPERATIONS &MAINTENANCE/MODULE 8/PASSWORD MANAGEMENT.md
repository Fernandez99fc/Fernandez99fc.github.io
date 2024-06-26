OBJECTIVES---------
Understand password management
work with the PASSWD and CHAGE command

PASSWD--------------
The passwd command can be used by any user to change their password
The root user can change any user's password

Some common passwd commands include:
passwd -l which locks the user account same as usermod -L
passwd -u which unclocks the user account same as usermod -U
passwd -e To expire the account
Passwd -d user - To delete user passwd

CHAGE COMMAND---------------------------
The chage command is use to modify password aging settings on a local user account.
Some common CHAGE commands are:
-W: To change warning days before password expiry
-E: Sets the expiry date for the user account
m: To change minimum days before password change
M: To change maximum password age or max days required to change a password

CHAGE -W 14 TEST- CHANGE WARNING DAYS TO 14
CHAGE -m 3 TEST - CHANGE MINIMUM DAYS REQUIRED BEFORE CHANGING A PASSWORD
CHAGE -M 99 TEST -CHANGE MAXIMUM DAYS REQUIRED TO CHANGE A PASSWORD

NOTE: WHEN AN ACCOUNT IS LOCKED AND YOU VIEW IT IN /ETC/SHADOW, IN CENTOS, IT BEGINS WITH DOUBLE "!!", WHILE IN DEBIAN IT IS "!$".