![Screenshot (89)](https://github.com/user-attachments/assets/fd65f679-4c8e-492c-9ae4-677a0b73b1ce)# SimpleCtf

![Screenshot (71)](https://github.com/user-attachments/assets/0389b598-3974-41b7-8d00-1c92738e32c9)

How many services are running under port 1000? 

![Screenshot (73)](https://github.com/user-attachments/assets/f37f52f8-d453-4b85-a950-9965fe8a7a5d)

Anw: 2. http and ftp

What is running on the higher port?

![Screenshot (74)](https://github.com/user-attachments/assets/d6936948-4804-457f-b746-010579a3f849)

-sC - Script scan
-sV - Service Version detection

Ans: ssh

What is the cve you're using against this application?
![Screenshot (77)](https://github.com/user-attachments/assets/8b0295fc-81b5-4fc1-ad47-528aad478c82)
![Screenshot (74)](https://github.com/user-attachments/assets/d6936948-4804-457f-b746-010579a3f849)

With a bruteforce, we could find /simple page on the website. Upon visiting, we see this page;
![image](https://github.com/user-attachments/assets/ff721e06-7976-48c5-9bc5-e04c58567fc1)

Which runs on cmsmadesimple version 2.2.8. 

We can check if there's an exploit for that using "searchsploit cms made simple"

![Screenshot (85)](https://github.com/user-attachments/assets/c49f1970-b71b-47d6-bbf0-25ea61172829)

we need an exploit for the respective version 2.2.8 and we can an sqli injection for version below 2.2.10.

using "searchsploit -m php/webapps/46635.py" to download.

Error:
![Screenshot (86)](https://github.com/user-attachments/assets/5e78a992-6464-43d4-8390-9d1901ec035c)

I got the error because I use python3 and changed few things in the sqli python program

Change the interpreter to python3;
![Screenshot (87)](https://github.com/user-attachments/assets/83df1da9-f0d8-4590-b55a-8b2c0795ec7c)

Add a parenthesis at the beginning and end(compare and add paranthesis to yours)
![Screenshot (88)](https://github.com/user-attachments/assets/58f73040-0a5d-49e6-9def-5829285abbc1)
![Screenshot (89)](https://github.com/user-attachments/assets/310c5a1b-25e3-4f2e-86b8-d704d90eaa7a)
![Screenshot (90)](https://github.com/user-attachments/assets/a0f8993f-32e7-479d-9b2b-fae1262d064e)

After running it againn, I still got an error but it returned a username "mitch" the previous time I ran it. I can use the ssh login checker module in metasploit to bruteforce since hydra cant handle the delay with the server and the python script also terminates connection due to delay.

After running the bruteforce, I was able to find a password for it called "secret"
