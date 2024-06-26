Every file has 3 time stamps:
TOUCH can also be used to modify the timestamps on a file:
-a change the access timestamps
-m Change the modified timestamps or modify the timestamps.
-d & t Set the timestamps to a specific date 
the format for specifying -t is ;
CCYYMMDDhhmm[.SS]

CC-FIRST TWO DIGITS OF THE YEAR
YY-LAST TWO DIGITS OF THE YEAR
MM-SPECIFIES THE MONTH
DD-SPECIFIES THE DATE
hh-SPECIFIES THE HOUR
mm-SPECIFIES THE MINUTE
ss SPECIFIES THE SECONDS

touch -a -m -t 203801191105.23 errorssh ----- CC YY MM DD hh mm. ss

NOTE: YOU CANNOT SET THE DATE BEYOND JANUARY 18 2038.
-r Copy timestamps from another file to a file.

TIMESTAMPS IS THE TIME AND DATE IN WHICH AN OBJECT WAS LAST INTERACTED WITH.

Ls can be used to view timestamps:
ls -lu to views access timestamps
ls -l to view the modified timestamps
ls -lc to view the changed timestamps

Easier to use stat command to see all the timestamps at once

vim(i to insert,esc to stop editing)
to save changes and quit(:wq)
to overwrite :qw!
u-undo
dd-to delete

OBJECTIVES:
creating files with TOUCH command,editing files with nano and vim,cheching timestamps of files and modifying timestamps of files using TOUCH...