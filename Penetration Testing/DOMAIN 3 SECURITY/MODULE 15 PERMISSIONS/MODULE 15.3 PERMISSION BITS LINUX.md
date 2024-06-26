In addition to standard RWX bits, there is a set of bits called permission bits.
Each bits has octal notation representation.
This is added to the front of  a file mode.

Set USER ID(SUID):4
Set GROUP ID (SGID):2
Sticky bit:1

SUID(SET USER ID)------------
The SUID bit is used with executable files. It runs the program with the permissions of the USER owner(U) instead of the user running it.
Most often used for programs root owns that must also run AS ROOT

The SUID bit shows up as an S instead of the execute permission letter for the User(U) permission bits on the file. For instance

- -rws r-x r-x .   1  root     root    50456    Jul 21 2020 /usr/bin/mount.

You can find all the files with a SUID bit by running this find command as root:
find / -perm /4000 - We are doing  a search in the root directory and we are specifying the permissions with thee number 4 because 4 IS THE OCTAL NOTATION FOR SUID.

SGID(SET GROUP ID)-------------------
The SGID has a different purpose for file and directory objects.
FILE: For a file, Linux runs the program with permission of the group owner (G) instead of the user running the program.
Directory: For a directory, group users inherit  the same permissions to all files in the directory: effectively creates a shared directory.

The SGID bit shows up as an S instead of the execute permission letter for The Group(G) permission bits on  a file or directory:
File: -rwx --s r--x   1  root slocate  48552  May 11 2019 /usr/bin/locate 
Directory:d rwx r-s r-x  2  root  systemd-journal  4096  jan 22  23:54

YOU CAN FIND ALL FILES WITH A SUID BIT BY RUNNING THIS FIND COMMAND AS ROOT:
find / -perm /2000- Doing a search in root with a permission that starts with number 2 and 2 is the octal notation for SGID......

STICKY BITS---------------------
It is used to protect files
--
This bit  is used by directories shared by groups
However, the files in this directory can't be deleted by any user except the owner or root
None of the group users can delete the files besides the owner

The sticky bits shows up as a T of the execute permission letter for the other(o) permission bits on a directory:
--
d rwxrwx rwt.  15  root   root  4096   Jan  24  18:07   tmp

YOU CAN FIND ALL FILES WITH  A STICKY BIT BY RUNNING THIS FIND COMMAND  AS ROOT:
Find / -perm /1000- Find files with sticky bit in the root directory with permissions starting with 1 because the permissions using 1 indicates that we are using a octal notation for sticky bit