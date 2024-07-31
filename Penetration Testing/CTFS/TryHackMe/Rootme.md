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













