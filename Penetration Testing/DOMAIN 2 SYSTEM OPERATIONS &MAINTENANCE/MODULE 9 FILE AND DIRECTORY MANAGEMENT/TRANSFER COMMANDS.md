OBJECTIVES-------
SCP(SECURE COPY) AND RSYNC
SCP-Used to transfer files to or from  a remote computer. Works with ssh

NOTE: Instead of manually adding an ip address of a system for scp or ssh connection,you can add the ip addr of the remote computer you're trying to connect to in /etc/host. <ip address> <name you wish to give it>. save. then ssh ip address name. it will connect automatically.

copying a file named "file1" from debian to my centos system
scp file1 sinzzu@192.168.0.162:/home/sinzzu
from centos to debian
 login to centos and copy a file from debian
scp sinzzu@192.168.0.162:/home/sinzzu/file1 file2

while secure copying a directory,-r must be used


RSYNC-Remote sync files or directories
rsyn -r copy directories
rsync -a to preserve timestamps`

note: To remove a file from a remote system we can use ;
ssh root@192.168.0.162 rm -rf /root/file1

rsync -azvh file1 sinzzu@192.168.0.162:/sinzzu
a-means to preserve the timestamps and permissions
h-nice readable output
z-will compress and make the transfer fast
v-verbose,shows you all the files being transferred
