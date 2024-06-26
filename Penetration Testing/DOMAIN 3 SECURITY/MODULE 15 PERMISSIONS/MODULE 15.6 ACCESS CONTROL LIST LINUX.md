OBJECTIVES------------------
Understand the purpose of ACCESS CONTROL LISTS(ACLs)
Explain how to identify an object with an ACLs applied
Use getfacl and setfacl commands to work with ACLs

ACCESS CONTROL LISTS(ACLs)
--
Access Control Lists are used to overcome the limitations of a basic linux permission. You can only apply permissions to a single account or a group with basic permissions.
But With ACLs, you can specify a list of multiple users or groups and their permissions. ACLs uses the same Read(r), write(w), execute(x) permission bits.

How can we determine if an object has ACL set on it?
--
Objects with the ACL have another character after the standard permission set - the period (.)
Directory with ACL: dr-xr-xr-x .
Link with ACL: lrwxrwxrwx .
File with ACL: -rw-r--r-- .

In CentOS most of the root level directories already have an ACL applied. This means any file created will inherit ACL 

SO WHERE DOES SOMEONE SEE AN ACL
--
By using the getfacl command :
getfacl <object>

WE CAN SET OR MODIFY AN ACL USING THE "SETFACL" COMMAND
setfacl -m,u,g,o:<name>:r,w,x<object>

For example, instead of adding user "sinzzu" to the group fernandez to have access to a file(Likewise,based on the permission), we can give access to sinzzu by :
setfacl -m u:sinzzu:rw <object>..m for modify. For instance the filename is "aclfile" we want sinzzu to have permission to .
setfacl -m u:sinzzu:rw aclfile

setting permission for other:
setfacl -m o:rw aclfile

To remove all changes from the file: you can simply do:
setfacl -b aclfile
