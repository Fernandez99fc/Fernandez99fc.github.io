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

* t: Number of threads to run

* -L: Specifies a file containing usernames

* -P: Specifies file containing passwords.

* -u: Try every user

* -f: Stop on first success

Using a rockyou password list can take forever to bruteforce with although it has the “letmein” password we found present in the list. In this case, I used a wordlist with fewer words to make things faster.
ACCOUNT LOGIN

We could only get the password for user account as we were unable to find for the root account. Let’s login with the password we found “letmein”.

After gaining access to the user account, there was pretty much nothing to do in there and we cant escalate privileges in it. The next step is to target another vulnerable service, I’ll take on nfs.

# NFS ENUMERATION

A system running nfs(network file system) service mostly likely has a share being hosted. Nfs is used for sharing resources like files, directories, printers and drivers to other nodes on the network and it runs on port 2049.

Use “showmount -e target.ip” to view nfs shares on the target.

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/ba736c15-981e-4812-b862-31275c7f0732)

/home/vulnix is a share hosted which is a home directory for a vulnix user .To acces the share, I will be use the mount command. I’ll create a directory on our local machine were we will mount the nfs share, in this case, I created a directory named nfsshare in our /mnt directory.

MOUNTING NFS SHARE

* mount -t nfs target ip:SHARE mount point.

* mount -t nfs 172.20.10.5:/home/vulnix /mnt/nfsshare
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/e4c3c23a-55d0-49eb-a02c-5bd8da80b429)

Visit the mount point where I mounted the share in /mnt/nfsshares.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/97afb823-7ae5-43cb-b9ef-e3d5c6b9556f)

We realized we don’t have permissions to access the share and only the vulnix user has access to it’s share. So what do we do? Well, we can think of creating a lookalike user on our local machine as the vulnix user hosting the share on our the target machine with the same user id(uid).

# GOAL:

Create a vulnix user account on our local machine having the same user id as the vulnix user account on the target machine, so that we will have access to the share just as the owner.

CREATING A USER ACCOUNT

use the command “useradd — create-home vulnix”. It creates the user “vulnix” and it’s home directory.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/db629bb6-485c-49c0-8475-9884c061d67f)
I created a user already.

We then need to edit the /etc/passwd file to change the uid for the vulnix user. We firstly need to know what the uid of the vulnix user is on the target system. Since we can login via ssh as “user” and we have it’s password “letmein”, we can check the vulnix user’s id with the command “id vulnix”.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/38551005-b94b-41f2-b9f0-e6a0f346c6a1)

On our system, we will edit the /etc/passwd file and change the uid of the vulnix user to 2008, I would also change it’s gid to 2008.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/edbc935f-2695-4b35-a214-bc3f75b2ad15)

Save the file and close. Switch to the vulnix user we created then change directory to the mount point /mnt/nfsshare, we should have access to it already.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/b4764ee3-a122-437a-8f3e-e2fe7a0e3a59)
vulnix home directory

We are now in the vulnix home directory but we are limited to the home directory, we can’t do anything much such as escalating privileges to the root user or editing the /etc/exports file. Executing a payload in that share will still limit you to the share, so there’s no point. What we want to do it to find a way to gain full access to the account.

# SSH RSA KEY AUTHENTICATION

One flexible feature ssh has is the use of publickey authentication, with this a client(attacker machine in this case) can copy it’s public key to the server(target) and the server stores it as an authorized key, so the client can log into the server without the use of a password.

To do this, we create an ssh public and private key with key-gen command and copy the public key to the share in the mount point.

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/b9ed6da6-2466-49db-9e0b-20bf6a54be4b)

* t: specifies key type
cd to the mounted shares and make a directory and name it .ssh, then copy the ssh public key from your vulnix/.ssh home directory to .ssh that we created.

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/7a576cdc-931d-4dd4-a7dd-950024bf548a)
Rename the id_rsa.pub file in the mounted shares to authorized_keys. Use the “mv” command to rename the file in the .ssh directory.

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/e149ab58-e8c9-46aa-8ccc-f6744e967e24)
After that, we should be able to login to the vulnix user account via ssh using the command “ssh -o ‘PubKeyAcceptedKeyTypes +ssh-rsa’ vulnix@172.20.10.5”

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/0f0870a5-4d58-49f2-bb3e-4277a6bc241b)



