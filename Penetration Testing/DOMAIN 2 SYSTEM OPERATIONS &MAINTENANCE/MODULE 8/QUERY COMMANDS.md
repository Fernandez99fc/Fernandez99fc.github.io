OBJECTIVES-----------------
UNDERSTAND QUERY COMMANDS USED IN LINUX..
USE THE COMMANDS ID,WHO,WHOAMI,W AND LAST

ID COMMAND--------------
The ID command is used to display account information on any user
id- displays information
It shows you the UID,GID and other groups you are in. It is useful while working with permissions
WHOAMI COMMAND----------------
Displays the name of the user you are currently logged in as.
It is always helpful to check who you are before you run a command that can be harmful (like rm!). If you logged in as root, you could accidentally remove an user's files.

WHO COMMAND-------------------
The WHO command displays all currently logged in users. Helpful to see how many users are on the account
WHO shows the  name,line or (terminal) and time . With the help of who -H ,you can view this
WHO -q shows the numbers of users.

W COMMAND----------------
The W command also displays all currently logged in users but also provides a system load output for each user. 
Why use this?
This is helpful when you have a system under heavy load and you want to see which user is taxing the system.
W displays the time in 24hrs, how long the system has been up for(time), how many users, load average

load average for the past 1 minute,5 minute and 15 minute
The JCPU time is the time used by all processes attached to the tty. It does'nt include past background jobs, but does include currently running background jobs.
login time or login@- The time the user logged in
The PCPU is the time used by the current process named in the 'WHAT' field
IDLE shows the time since the user last interacted with the system

THE LAST COMMAND........
The last command shows a list of the last logged in and out users. Last searched back through the /varlog/wtmp file and displays the list of all logged in and out users since that file was created.

To show the last two logins. we will use last -2.
last -2 F -full information about the login and log out time of the session for the last two logins
lastb- shows a log of failed/ bad login attempts. maybe someone is trying to remotely access your sysem,trying to login or trying to bruteforce its way in.
Why use this??
This is helpful with trying to track down a user activity on a system

NOT DONE.............................................................................................

