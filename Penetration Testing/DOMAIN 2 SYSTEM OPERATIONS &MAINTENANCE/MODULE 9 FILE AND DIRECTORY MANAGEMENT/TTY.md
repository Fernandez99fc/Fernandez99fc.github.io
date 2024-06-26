
1.  CTRL + ALT + F1 – TTY1
2.  CTRL + ALT + F2 – TTY2
3.  CTRL + ALT + F3 – TTY3.
4.  CTRL + ALT + F4 – TTY4.
5.  CTRL + ALT + F5 – TT5.
6.  CTRL + ALT + F6 – TTY6.

Multiple users can work on a linux/unix system without at the same without physical access to the system.This is with the use of the 6 virtual terminals present in unix based systems,which is tty1- and, tty7 is the one we've using in linux. You can switch between the 6 virtual terminals using each terminal keys.
pts stands for pseudo terminal secondary and tty means Teletypewriter. tty and pts are connections to a computer. pts includes ssh,telnet e.t.c.
Tty means any terminal in Linux/Unix system.

PTS is initialized when there is a remote connection. TTy signifies active virtual terminals. Pts/0 is for graphical connection- It is the connection for CLI

Back in the days, terminals were physical device connected to a serial port each. These shows up in UNIX as 'device files' in /dev.
There are two different types of virtual terminals. The first set are those connected via display. These are "tty0", "tty1".
Then there is a concept of a pseudo terminal. One is required for each "SSH " session that you use to connect to your system, and one for each (Gnome) X terminal session. These are the "pts/n" names. search for the pseudo terminal to know more..


