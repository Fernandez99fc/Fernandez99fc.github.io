OBJECTIVES --
Understand inodes,symbolic,hard links, the differences and relationship between them.
use ln command to create symbolic and hard links
use the unlink commands..

Every linux file or directory has a name,data block and an index number which is known as inode
Linux uses inode number to access the files
a file is assigned an inode number when created by the file system

HARD LINK--
can have one index number or inode but can have two different file names.
Both files names point to the same inode on the file system.

When a hard link file is created, it points to the same spot on a hard drive with the original file. They would have the same inode numbers since they're on the same spot in a hard drive and can take different names. let's take for example file1 and file2, if file1 is being modified, file2 automatically becomes modified too.
In hard link, both files share the same data. If file 1 gets deleted, file 2 won't get deleted.

SOFT LINK OR SYMBOLIC LINK OR A SYMLINK----
A soft link points to the actuall file holding the data. The original file holds the data not softlink, soft link acts as a pointer to the original file holding the data. Once the original file is deleted, symlink gets deleted too because it relies on the original file

For symlink, file1 and file2. file 1 points to a spot on the hard drive to store it's data, unlike hard link where two files point to the same spot on the drive,when you create a symbolic link  "file 2", it points to file1(the descriptor) instead of pointing to a spot on the hard drive.

Just like a shortcut of a file in windows pointing to the original file, that's how a soft link operates but they have different inodes.

HARD LINKS                                                                VS                                    SOFT LINKS
In Hard links,both files share the same inode                                     Data file and symlink have different inodes
In Hard link,both files share the same data                                        Data file and symlink do not share the data
in Hard link,both files must be on the same file system                    Files can be on different file systems

HARD LINK--
"ln" is used to create a hard link file
ln "original ifile" "hard link file"

now that we've created our hard link file,we can check the inode numbers of the files we created
using 
"ls -il file*"- this gives us the inode number and a long listing of all files having the name file and the * will include files having something after the name "file".
"i"-gives us the inode number
"l"-gives us a long listing
The number at the left is the inode number

SOFT LINK--
ln -s-"s" for symlink
symlink or symbolic files are light blue.
symlink points to the data itself using the arrow sign

unlink <filename> to unlink or use rm

