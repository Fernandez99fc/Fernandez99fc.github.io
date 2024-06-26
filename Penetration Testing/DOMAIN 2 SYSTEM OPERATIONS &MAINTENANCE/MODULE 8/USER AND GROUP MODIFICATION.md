OBJECTIVES----

UNDERSTAND USER AND GROUP MODIFICATION
WORK WITH USERMOD AND GROUPMOD.

USERMOD COMMAND-----
It is used to modify an established user account

What do you do when you forgot to add a user to a group on creation? Usermod!
common usermod commands- Usermod -aG(add append) an additional group
"-a"-append.."a " appends  a user to a group,without "a",the specified group will overwrite the previous groups you were in
"-G"-additional group

sudo usermod -aG <wheel> user- Will add user to wheel group to be able to escalate privileges inCENTOS
sudo usermod -aG <root> user- Will add user to the "root" group and have priviledges and permissions in DEBIAN BASED
USERMOD gives priviledges and permissions and adds a user to a group.

/etc/shadow -Stores passwd of users in encrypted format
grep juwon /etc/shadow- shows the specified user's field and its encrypted password starting with a "$"
if the account is locked using usermod -L user- the /etc/shadow of the user starts with "!$" or an exclamation mark then a $ sign
Usermod -L- Lock a User account.
Usermod -U - To unlock

GROUPMOD COMMAND-------
used to modify an existing group account
What do you do when you need to change a group name. groupmod!

common groupmod commands:
groupmod-n -To change the group name
groupmod -n <group name> <new name>
groupmod -g -To change the group ID
groupmod -g <Group Id> <group name>


