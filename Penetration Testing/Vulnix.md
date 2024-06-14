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
After reading the blog page and the documentation, I realized the page is being hosted on http://kioptrix3.com. and it has a page for gallery in kioptrix3.com/galley.

After visiting kioptrix3.com/gallery, I found nothing useful there.

![VirtualBox_LINUX SERVER_23_04_2024_20_53_42](https://github.com/Fernandez99fc/cybersec/assets/172477285/2a67190c-0016-4de6-8bae-0428e32e46dd)

But there's a login page right beside the blog.
![VirtualBox_LINUX SERVER_23_04_2024_20_56_08](https://github.com/Fernandez99fc/cybersec/assets/172477285/3e2c400b-059e-4864-ab4e-add22e895400)

Noticed the page is powered by lotuscms which is a type of contents management system that is used to create and manage contents on a website. We can check if lotuscms has any known vulnerability with metasploit. 

![VirtualBox_LINUX SERVER_23_04_2024_21_02_09](https://github.com/Fernandez99fc/cybersec/assets/172477285/6b7cb7e5-ed11-42e4-b083-4e68cacb8da0)

Found an exploit "lotus cms 3.0 eval remote code execute". Using show options command to view available options for the exploit. I Set rhost to target ip, changed URI and changed the payload to generic/shell_bin_tcp.
![VirtualBox_LINUX SERVER_23_04_2024_21_09_50](https://github.com/Fernandez99fc/cybersec/assets/172477285/e932de46-35bf-4304-b05f-7f78631818e2)
This exploit will execute a remote code in the lotuscms and create a bind shell from the cms.
![VirtualBox_LINUX SERVER_23_04_2024_21_12_58](https://github.com/Fernandez99fc/cybersec/assets/172477285/8a967676-870b-40ca-9d2f-2a2fc56e4a8b)

After gaining a shell, I ran "python -c import pty; pty.spawn("bash")" to expand the interactive shell.
![VirtualBox_LINUX SERVER_23_04_2024_21_46_45](https://github.com/Fernandez99fc/cybersec/assets/172477285/3a557098-efb0-4241-ab07-c29865f08b7e)
After searching through the system, I found some user accounts in the /home directory. Then searching through each of them, I was able to find a gconfig.php file in the www kioptrix.com/gallery home directory. Gconfig is a file used for storing data such as usernames and passwords in mysql database.

We could see some credentials of the root user being exposed. We will try to login with that.

![VirtualBox_LINUX SERVER_23_04_2024_21_56_18](https://github.com/Fernandez99fc/cybersec/assets/172477285/c7f78b09-7a09-448a-ab41-3b2469c6537d)


 




