OBJECTIVES---------------
Understand the purpose of umask
Explain how umask is configured
Determine where umask should be set 

In Addition to to ownership, an object is created with certain default octal permissions, by default Linux uses 666 for files and 777 for directories but mostly according to the user's umask being set..
As we said, when a file is created, it doesnt get the full permission, the default is rw rw rw(666) and for directory rwx rwx rwx(777)

If we want user and group owner to have full access to a file and user and group only should have full permission to a directory, we can simply do:
umask 006
rw- rw- --- For a file
rwx rwx --x for directory

OR

umask 001
For file - rw- rw- rw
for directory drwx rwx 

UMASK is the opposite of giving a permission.
But when we created a file, the files has 664...Why is that ?
It's because  of the user mask(UMASK) set for the system which we can see by just typing "UMASK"

The UMASK removes bits from the default Linux Permissions; this gives a system default of :644 for files and 755 for directories.

UMASK PERSISTENCE
--
Changing UMASK on the command line is just for  a temprorary change during the session. It is useful when you're creating a lot of files or directories .

WHAT DO YOU DO WHEN YOU WANT TO CHANGE UMASK PERMANENTLY
--
The UMASK settings are configured in the /etc/profile upon user type.  Specifically in /etc/profile you will see the line: UMASK 002. Changing this line will permanently change the UMASK.

