# Vulnhub: Vulnix Walkthrough

Hello everyone, I decided to share my walkthrough on how I solved the vulnix challenge from hacklab.

Link: https://www.vulnhub.com/entry/hacklab-vulnix,48/

Goal: Boot up, find the ip address and hack into the root account by any means to retrieve the trophy.

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/8403ea1c-1399-4afc-abdf-1a185c3d2d56)

After downloading the box and setting up it’s networking features, we are good to go!

# ENUMERATION

This is the most crucial phase in a penetration test where we gather information about the target. We don’t know the ip address of the target system. They’re various ways of getting the ip of the target, but I’ll stick with arp-scan in this case as we are on the same network.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/4ab517b5-8366-49ef-97e1-0db2391f4237)
arp-scan — interface=eth0 — localnet

— interface: Specifies the interface, replace eth0 with wifi if you’re on a wireless network.

— localnet: Indicates that we are scanning from a local network.

Target ip: 172.20.10.5

# SCANNING

I will be using nmap to scan the target ip to find open ports and other useful info such as service version and Os detection.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/97d2f0b2-7459-4979-87fa-593e19980641)
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/68543839-2e55-458b-855a-4b3755a09bc0)

We have a lot of open ports, I’ll start off by exploiting the most common ports, ssh, nfs,smtp, finger before I explore other services.
# EXPLOITATION

# SSH

The ssh version is 5.9p. I’ll be begin by checking if the ssh version is vulnerable to any exploit using metasploit. You can also use searchsploit.

I was unable to identify any exploit for that version of openssh using metasploit, but I tried out the available modules for openssh. I will be using auxiliary/scanner/ssh/ssh_enumusers which that version of openssh seems vulnerable to. This module performs user enumeration which helps us get the users available on the system.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/ce0c389b-a360-4c0b-87a8-938ffe5b01aa)
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/38c76c45-11c1-4998-b8f2-612af487fad8)

I set the rhost and user_file parameters. Then type run or exploit.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/4a78840f-c71b-4a86-a1a0-d4ac527222b7)

I was able to find users: root and user.

# BRUTEFORCE

Since 2 user accounts were found, I will run a bruteforce attack against them using Hydra to try and find the password using a wordlist.

I created a file and named it “unixnames” then added those 2 user accounts we found, the remaining accounts are system accounts and they’re useless in this case.

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/8cba405b-2e97-4d9a-b730-0174bce92d3a)

hydra -t 3 -L unixnames -P passwords -u -f 172.20.10.5

t: Number of threads to run

-L: Specifies a file containing usernames

-P: Specifies file containing passwords.

-u: Try every user

-f: Stop on first success

Using a rockyou password list can take forever to bruteforce with although it has the “letmein” password we found present in the list. In this case, I used a wordlist with fewer words to make things faster.
ACCOUNT LOGIN

We could only get the password for user account as we were unable to find for the root account. Let’s login with the password we found “letmein”.

After gaining access to the user account, there was pretty much nothing to do in there and we cant escalate privileges in it. The next step is to target another vulnerable service, I’ll take on nfs.
