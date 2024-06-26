OBJECTIVES--------
Understand how files and directory permissions work
Explain how files and directory permissions are constructed.
Explain the component of the permission syntax(RWX, UGO AND OCTAL NOTATION)

Files and directory permissions are the primary security characteristics in Linux.
All files and directories have permissions set and an owner set.
The permissions defines how users can access resources on a system.

READ(R), WRITE(W) AND EXECUTE(X) PERMISSIONS------------
Each object(file or directory ) has a permission made up of read(r), write(w) or execute(x) permissions.
You can see this on objects when you run "ls -l". It displays the file or directory permissions with other information.

USER(U), GROUP(G) AND OTHER(O) PERMISSIONS-------------
Each object(file or directory) belongs to a user owner(U) and a group(G) owner. Additionally, you can also set an Other(O) permission.
The Other(O) permission is ther permission for anyone other that the user and the group.

These are represented in the repeating rwx permissions. For instance a file named "TEMPLATE 1" has the following variable:
- - rwx -wx r--     1     rob       rob       0     Nov     30     21:24      template

user       group    other
rwx         -wx        r--
Together, this permissions make up the object mode.

OCTAL NOTATION-----------
Octal notation represents permission with numbers:
read-4
write-2
exexute-1

Numbers are summed to give a numeric permissions to the user, group and other. Using the file "TEMPLATE" example again.
user   group   other
rwx    -wx       r--

user                      group            other
rwx=4 + 2+ 1=7, -wx=2 + 1=3, r--=4 
Therefore, the octal notation for the file is 734.

