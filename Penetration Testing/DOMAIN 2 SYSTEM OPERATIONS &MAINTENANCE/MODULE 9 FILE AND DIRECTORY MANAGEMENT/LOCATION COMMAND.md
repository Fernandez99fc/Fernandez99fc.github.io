OBJECTIVES----------------------------------

Tools to find and locate files and directories like find,locate,which,updatedb,whereis

FINDr3
find / -means whole directory
find /. or find /home means in the home directory.

find / -type f -name "file1" -user root   --finds the file "file1 " in the whole root directory.
find / -type f -size 30k -name "*.txt"-finds  a file of 30kilobyte in the whole directory ending with txt
find /home -type d -perm  777 - finds a directory having the permission 777
find /home -type d -perm u=rwx,g=rwx,o=rwx- finds a directory having the permission 77
find / home -type f -amin 30 - finds files accessed 30 minutes ago
find / home -type f -mmin 30  find files modified 30 minutes ago
find / home -type f -atime 2 find files accessed in last 2 days
find / home -type f -atime 0 find files accessed in 24hrs

LOCATE COMMAND--------------
to check if locate is installed on the system we use which locate
first thing to do is to update the database it relies on. "sudo updatedb"
locate file-locates the file file1

WHICH COMMAND-----
It is use to determine the the location of a program or command. example:
which "lsblk"- tells us where the command belongs to in the file system hierachy

WHEREIS COMMAND----
Gives us the file hierachy of  a program or command and it's where we can find it's manual page.
whereis locate- gives information of where locate is and where you can find the man page of locate
whereis -b locate-b stands for binary. locates the binary path for locate
whereis -m locate- shows the path of the manual for locate