OBJECTIVES------
UNDERSTAND USER AND GROUP QUOTAS IN LINUX
WORK WITH COMMANDS LIKE EDQUOTA,QUOTA AND REPQUOTA

Once we've enabled quotas on a filesystem, we must create quotas on  a user or group. 
To create quota for a user with the edquota(edit quota)command, we will use edquota -u(user) <user>
To create quota for group, edquota -g <group>

The QUOTA file opened for the user allows you to set a soft and hard limit on blocks and inodes.
The BLOCK limit specifies the maximum number of blocks a user can fill
blocks           soft             hard
   0                    0               0
   NOTE: The blocks column shows the numbers of blocks currently in use by the user - this number cannot be edited.

An inode limit specifies the maximum number of files a user can create 
blocks         soft           hard
0                    0                 0

The inode column shows the number of files currently in use by the user - this number cannot be edited...

A SOFT limit is limted  by a grace period(in days).  A user can go on creating files or adding blocks until the grace period is up.
If the user exceeds the soft limit, they get a warning.

A HARD limit is just that -a hard stop.
The user gets an error message 
users cannot fill any more blocks or add any more files once this is reached.

If you choose to set a soft quota, you must configure the grace period using edquota -t

The quota command is used to display the quota for a user and group
quota -u <user>
quota -g <group>

The REPQUOTA(REPORT) COMMAND can be used to display report on the quotas on a file system:
repquota <mount point>.
Alternatively, you can report on all file systems:
repquota -a