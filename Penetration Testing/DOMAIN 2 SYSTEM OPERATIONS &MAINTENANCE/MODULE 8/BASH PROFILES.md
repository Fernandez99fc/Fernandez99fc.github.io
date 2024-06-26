OBJECTIVES------------------
Understand the purpose of bash configuration files.
Work with files and directories:
/etc/profile
/etc/profile.d
~/.bash_profile
~/.bashrc
~/.bash_logout
~/.profile

The terminal provides a shell.
When a terminal is lauched, it searches for the .bash_profile. That is if the terminal uses bash shell. For tcsh, if the terminak uses tcsh shell, it looks for the .login config file........
When you want to create environment variable, bash uses export var=value while tcsh uses $etenv vae value.
bash uses 2> and tcsh uses >&.

For instance, my debian distro uses zsh and my centos uses bash.

When using a shell program, you can configure options, variables and aliases. more of it will be covered in module 25 BASH SCRIPTING.
The thing to note is that settings like aliases, options and variables are not persistent unless they reside in a configuration file. 

When a user logs in, the very first thing that gets done is the /etc/profile gets read. It is called the global configuration file
The files under the /etc/profile.d are read as well....
/etc/profile.d- This directory holds configuration information for various shell types.

NOTE; If you want to make any changes in the /etc/profile, you can simply create a file ending with .sh in profile.d and when the system boots up, it will be read.
.bash_profile,.bashrsc e.t.c If theyre in the user directory they are considered user entry. /etc/profile,/etc/profile.d are considered global entries. 


BASH  VS SHELL VS TERMINAL VS COMMAND LINE VS CONSOLE
/SHELL- shell is  a program that takes the command we input and gives us an output. Whenever our terminal is initiated, shell is also loaded
TERMINAL- A terminal windows , terminal emulator. It is a text only windows in a graphical user interface that emulates a console.
COMMAND LINE- command line is an interactive interface for running commands
BASH IS  A TYPE OF SHELL
CONSOLE - IS A COMPUTER WITH A KEYBOARD FOR ONLY COMMAND LINE.

We have different types of shell:
bourne shell(sh)
korn shell(ksh)
bourn again shell (bash)
POSIX shell(sh)
C shell (csh)
tcsh
