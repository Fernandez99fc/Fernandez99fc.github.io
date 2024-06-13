# Kioptrix 1.2

LINK: https://www.vulnhub.com/entry/kioptrix-level-12-3%2C24/

Type: Web application

# Enumeration
 Target Ip: 172.20.10.7
 
 Using Nmap to scan the target:
 ![VirtualBox_LINUX SERVER_23_04_2024_20_24_59](https://github.com/Fernandez99fc/cybersec/assets/172477285/25555fe8-cd02-4c36-b1ab-1f425c176d5a)
Two open ports found are ssh(port 22) running version openssh 4.7p1 and http(port80) running apache httpd 2.2.8 as the service version.

I have tried logging into the ssh server,but it didn't work. I'll have to try visiting the apache server running on http(port 80) in my browser. Firstly, I'll add the target ip to the /etc/hosts file to be resolved into the domain being hosted on the server. I named it koiptrix3.com
![VirtualBox_LINUX SERVER_23_04_2024_20_44_06](https://github.com/Fernandez99fc/cybersec/assets/172477285/bdcc1795-c4bb-48b8-87a7-da92aa588a66)
After reading the blog page and the documentation, I realized the page is being hosted on http://kioptrix3.com. and it has a page for gallery.




 
 




