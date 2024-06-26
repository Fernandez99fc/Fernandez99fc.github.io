OBJECTIVES-------------
Understand user and group creation
Use the useradd and groupadd commands

USERADD---
The user add command is used to add local users to a linux system
It creates an entry in /etc/passwd and /etc/shadow
User accounts ID begin at the number 1000

Useradd uses 3 files to create a user:
/etc/default/useradd-Creates and contains default user variable settings. 

/etc/login.defs-This file provides default configuration information for several user accounts. The userdel,useradd,groupadd,usermod takes default values from this file.

/etc/skel-It is a directory that Contains default home directory files and directories in the home directory for each user. It is used to initiate a home directory when a user is created and it's default files including .bashrc e.t.c and ensures that all users begin with the same settings and environment stored in the files....

useradd -m ="m" should be specified to create a home directory for the user being created if the "CREATE_HOME " is not set to YES in /etc/login.defs
NOTE: Debian based distributions don't have CREATE_HOME by default,so we have to specify it to create a home directory

This directory creates 3 files:
.bash_logout
.bashrc
.bashrc.original
They are in the home directory of every user

NOTE: /etc/skel is called the global entry by COMPTIA.

GROUPADD-------
It's a command used to add a group to a linux system
it creates an entry in the /etc/group
groupadd -g 1337 best- creates a group named "best" with the group ID 1337

NOT TO BE PROMPTED FOR PASSWORD USING SUDO,ADD USER TO KALI-GRANT-ROOT GROUP