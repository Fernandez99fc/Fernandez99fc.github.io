OBJECTIVES------------------------
Locate files related to user and group management.
work with /etc/passwd, /etc/shadow, /etc/group

/ETC/PASSWD------------
The /etc/passwd file holds the information on all the users on a system. Each Line in /etc/passwd is a record for a user and each line has  seven fields delimited by a colon or ":"

/ETC/SHADOW-----------------
The /etc/passwd file stores passwords of user accounts. It also stores password ageing information. Each Line in /etc/shadow is a record for a user and each line has  eight fields delimited by a colon or ":" character.

The last few colons of numbers in /etc/shadow signifies:
For examples:
18736:0:99999:7:::
18736 represents The day since the epic time and the epic time in a linux system is january 1 1970

0 represents the minimum days required for a password to be changed or before a change can be allowed

99999 represents the maximum number of days a password is valid for

7 represents the numbers of days that a user will warned before a password expires. this happens few days before the password expires,in our case , we still have 99999 days for our password usage.

/ETC/GROUP----------------
The /etc/group file contains information on groups in linux. Each Line in /etc/group file is a record with four fields delimited by  a colon

NOTE: "x " in /etc/passwd means the user has  a passwd and it's stored in /etc/shadow.
