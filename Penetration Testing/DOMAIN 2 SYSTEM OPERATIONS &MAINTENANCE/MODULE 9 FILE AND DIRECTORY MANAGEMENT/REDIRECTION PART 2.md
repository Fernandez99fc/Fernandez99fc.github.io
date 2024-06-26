OBJECTIVES---------------------
Redirect command output to another command
Understand the purpose of /dev/null and /dev/tty
working with tee and xargs commands

REDIRECTING COMMAND OUTPUT TO ANOTHER COMMAND
ausearch -i | grep -i "ps4" name1
cat name1 | grep -in "ps4" name1

DEV/NULL------------
/dev/null can be used to discard redirected ouput,errors or texts to it. It is Suitable to use when running commands and you dont want to see the displayed error,you can simply redirect the error using (stderr or 2> )to dev null. 
Example grep -i food ./* 2> /dev/null- If the word "food" was found in any file in the home directory,the output will be printed out and the error will be redirected to /dev/null.
Check this out--
find . -type f -size -130k -name "*.txt" &> /dev/null- It redirects both stdout and stderr to null and get discarded in /dev/null

1.  CTRL + ALT + F1 – Lockscreen. (tty1)
2.  CTRL + ALT + F2 – Desktop Environment.
3.  CTRL + ALT + F3 – TTY3.
4.  CTRL + ALT + F4 – TTY4.
5.  CTRL + ALT + F5 – TT5.
6.  CTRL + ALT + F6 – TTY6.

pts stands for pseudo terminal secondary and tty means Teletypewriter. tty and pts are connections to a computer. pts includes ssh,telnet e.t.c.
Tty means any terminal in Linux/Unix system.

Back in the days, terminals were physical device connected to a serial port each. These shows up in UNIX as 'device files' in /dev.
There are two different types of virtual terminals. The first set are those connected via display. These are "tty0", "tty1".
Then there is a concept of a pseudo terminal. One is required for each "SSH " session that you use to connect to your system, and one for each (Gnome) X terminal session. These are the "pts/n" names. search for the pseudo terminal to know more..

tty0 represents the system console
tty1 represents a physical console or graphics shell
tty3-text shell
tty-To check the tty we are in
dev/pts/0 shows that we are in the sudo tty terminal

pip or | is used to pass a command to another command
xargs- It can be used to give more information of a searched file or directory
		find . -type f -size -140k -name "*.txt" | xargs ls -l- Gives more info of any file having .txt in the working directory 