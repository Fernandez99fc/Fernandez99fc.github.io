# Bind Shell vs Reverse Shell

A shell is simply a program which is used to execute commands on an operating system.  Examples of shells in linux include /bin/bash(default), /bin/zsh, /bin/sh e.t.c and cmd/powershell in windows.

A Bind shell allows an attacker to connect to a netcat listener running on the target machine. Hence, providing it with a remote shell. In other words, a netcat listener has to be running on the target system configured with a shell.

In most cases, inbound connections to a system is being blocked by a firewall which prevents the attacker from connecting to the netcat listener on the target system, this is where reverse shell comes to play. 

Reverse shell does the opposite of bind shell, instead of connecting to the netcat listener on a target machine(inbound), the target machine connects to the netcat listener on the attacker's machine(outbound). Most of the times, outgoing or outbound traffics are not being blocked by firewall because the system has to interact with various services outside the system e.g http,https.

# Bind Shell

Attacker's Ip is **192.168.0.122** running linux
Target Ip is **192.168.0.156** running windows

To create a bind shell to the target system, the target has to have a netcat listener listening for connection on a port with a shell to execute, then the attacker connects to it. 
But we have to setup a listener first on the target:
![[VirtualBox_windows 7 64x_29_06_2024_17_41_40.png]]
                                    Target Machine
-  - l - To listen
- - v - For verbose
- - p - Specify port to use
- - e- Program to execute(e.g cmd.exe/powershell)

Attacker's Machine:
![[VirtualBox_LINUX 2023_29_06_2024_17_51_26.png]]
We now have a bind shell. Type "dir" to list directories.

# Reverse Shell

We create a listener on our own system and the target connects it to, same process with bind shell, just that we are hosting a listener on our system and not the target.
Step 1: Create a listener first 
Step 2: Connect from target system

**Note**:  A listener has to be setup first else you see a connection refused or no port available error, this is because what we are connecting to has to be active first before relaying a request.

![[VirtualBox_LINUX 2023_29_06_2024_17_58_29.png]]
- - l - To listen for connection
-  - v - Verbose
- - p- Port
- -c - To specify shell program

"- e " flag is used in windows to specify shell, while "- c " is used in linux.

![[VirtualBox_windows 7 64x_29_06_2024_18_00_01 1.png]]We now have a bind shell to the attacker's machine.

Most of the time, a reverse shell is preferred to a bind because you don't have access to the target's system to enable netcat or you dont know if there's netcat installed or running, and a firewall might be blocking incoming traffic.



