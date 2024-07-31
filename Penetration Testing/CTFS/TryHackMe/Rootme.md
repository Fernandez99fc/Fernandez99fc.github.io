# Rootme
![Screenshot (67)](https://github.com/user-attachments/assets/1eee0164-0b31-4f27-b179-1c070584a394)

# Network Scanning
![Screenshot (47)](https://github.com/user-attachments/assets/177c03ec-c280-4488-8f56-1abaae05f654)

-sC - Enable script scan

-sV - Service version detection

--min-rate- minimum rate of data to be sent.

![Screenshot (50)](https://github.com/user-attachments/assets/d30495c9-cadc-4107-9668-6bdb6238ed76)

Two open ports are ssh(port 22) and http(port 80 running apache server).

By visiting the ip address in a web browser on port 80, we see this page with the text;
![Screenshot (48)](https://github.com/user-attachments/assets/feee856d-da92-4856-8120-d10d6862716a)

By Viewing the page source, we don't find anything interesting;
![Screenshot (49)](https://github.com/user-attachments/assets/be02b7cf-3c1c-49eb-a033-e6eff4b37e1d)

Using gobuster to scan for hidden files and directories:
![Screenshot (51)](https://github.com/user-attachments/assets/67e9ed13-7165-4a48-bc18-b348b5240390)

Two useful directories found were /uploads & /panel

we noticed /panel provides us with a page to upload contents, while /uploads contains uploaded contents or files from /panel.

By visiting panel, we see this;
![Screenshot (52)](https://github.com/user-attachments/assets/3348ac9c-8b4b-4f36-9d95-aa75a70af57d)

We can upload any file, but the goal is gain access to the web server, we can think of uploading a malicious code to get  a reverse shell.
But I noticed that the server does not accept .php file extension, uploading .html file will make it a text file and not an executable, so we can use the .phtml(php html) which is another web file extension and makes our payload executable.

Using msfvenom to generate a php payload;
![Screenshot (66)](https://github.com/user-attachments/assets/1f23cb77-331d-46a1-b91c-36473abcbeda)

![Screenshot (68)](https://github.com/user-attachments/assets/e9d2caf3-b07f-4f07-85ec-f82cc533c6aa)

![Screenshot (53)](https://github.com/user-attachments/assets/706f9a79-c35e-496b-a08a-16531697aff8)

Upload the payload, after uploading, start a netcat listener;
![Screenshot (65)](https://github.com/user-attachments/assets/0327f6d1-c802-4d10-8d58-df01da0abe43)

Navigate to /uploads and execute the payload;
![Screenshot (70)](https://github.com/user-attachments/assets/0de5865e-6a5f-422f-8bed-b5342cc4bccc)

We have a shell;
![Screenshot (69)](https://github.com/user-attachments/assets/0d70fdf0-bbcb-4aef-8be1-e2f298f54f48)

We can see the user.txt file and read the text.

Next, we need to escalate privilege to the root user. We need to find setuid binaries which are executable we can run with the right of the root user. we can do "find / -perm /4000 2> /dev/null"
![Screenshot (62)](https://github.com/user-attachments/assets/2e2879bd-ece4-4ef0-ac92-974d7a83903a)

We can't make use of sudo and the only useful binary to use to escalate privilege is the /usr/bin/python program.

we can use this command to escalate privileges: python -c 'import os; os.execl("/bin/sh", "sh", "-p")' 

gotten from https://gtfobins.github.io/

![Screenshot (63)](https://github.com/user-attachments/assets/b6484adb-263b-4864-8a66-e6ba9449d757)

using pwd shows we are in the root directory and we read the root.txt file

Happy hacking folks!














