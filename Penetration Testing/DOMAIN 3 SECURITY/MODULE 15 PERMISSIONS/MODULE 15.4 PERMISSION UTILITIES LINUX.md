OBJECTIVE--------------------------
Understand how permissions are modified
Explain how ownership is modified
Use the chmod,chown and chgrp commands

SETTING AND MODIFYING PERMISSIONS WITH CHMOD...
Permission modifications are done with chmod (change mode) command. accepts octal or symbolic notations.

Symbolic Notation uses UGO,RWX to indicate permissions as well as A to change permission for ALL.
(+) to add permissions
(-) to remove permissions
(=) to set permissions....

For example to set user owner(U) to read and write and set group(G) and Other(O) to read only on file.txt:
In the octal form:
---
chmod 622 file.txt
symbolic:
chmod u=rw-,g=r--,o=r-- file.txt

MODIFY OWNERSHIP WITH CHOWN AND CHGRP
--
Modification to file and directory ownership are done with the chown (change ownership)command
Chown accepts user and group owner seperated by a colon(:) or period(.). Both are valid:
chown user:group file.txt
chown user.group file.txt

You can also specify just the user owner or group owner:

chown user file.txt
chown :group file.txt- using the colon enables chown to understand that you're modifying a group.

To change both the user owner and the group owner to the primary group of the user owner:
chown user:file.txt....In other words, without specifying the group, it changes the group owner with the user owner..
chown -R(recursive change)- -R changes the directory's ownership, sub directories and sub files.

MODIFY GROUP OWNERSHIP WITH CHGRP
The CHGRP can be used to change just the group assigned to an object.
CHGRP takes the name of the new group and the object to change.

For example a directory , dir1, can be modified by root using the chgrp command:
dir1 currenlty belongs to the group user sinzzu and group sinzzu.
Now the group needs to be changed to fernandez: chgrp fernandez dir1
now when we use ls -l,we see: sinzzu fernandez dir1


DEMO TIME
chmod 4766 file.txt- we want to have a file executable and should be able to run by any user as me,and the group and other should be able to read and write.
4 is the SUID,7 refers to the numberical permission for user to be able to (rwx) but using 4 replaces the execute(x) to s. 6 refers to group permission which is read and write(rw). 6 also refers to read and write for other.

NOT DONE..............