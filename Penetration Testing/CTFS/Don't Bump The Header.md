# Ctflearn: Don't Bump The Header
* Link: https://ctflearn/challenges/109

* Difficulty: Medium

* Objective: Try to bypass my security measure on this site! http://165.227.106.113/header.php

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/43ea6ff7-57e7-41d6-8424-ef0f91470e35)

The first step is visiting the website http://165.227.106.113/header.php.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/8e440724-d1b0-43e0-a2db-9348d05919d3)

When we visited the url, we saw an error message displayed indicating that our user agent is not correct and we can’t access the website, also telling us the version of the user-agent that is in use, which is mozilla 5.0 running on linux.

By viewing the page source, we get this:
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/21887d77-d561-43cf-bea9-dff77f05790a)

Seems the website doesn’t want us to have access because we are not using it’s preferred user-agent “sup3rs3cr3tag3nt”. What can we do? Well, we can try to intercept the http traffic and modify the http request with burpsuite and changing the user-agent to “sup3rs3cr3tag3nt” to see if we can gain access.
![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/8ec02893-7f4b-439f-81c1-08ae75fa6c2e)
* Before modifying

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/09dcf5c1-cbc3-49d4-a2cf-8cf3145465da)
* After Modifying

If you take a look at the user-agent, you’ll see I changed it to the preferred user-agent it’s requesting for. With that been changed, we can now forward the traffic to the destination website and let’s see what we have.

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/698e7942-6650-4a11-84ec-ecd35584116b)

Here we are again, it’s saying it seems our request is not coming from awesomesauce.com website. In order words, our request has to come from awesomesauce.com. We need to process our request like it’s coming from that website, by modifying the http request and adding a “Referrer” line as a header in the body.

Firstly, we need to reload the website and forward the request to a “repeater” by right clicking and selecting “forward to repeater”. This is where we will be modifying the traffic and forwarding to the server to see the response we get.

After that, we will again change the User-agent header to what we changed it to previously, then add a “Referrer” line at the end of the request. Then click on send.

![image](https://github.com/Fernandez99fc/cybersec/assets/172477285/48ff2a80-cf69-4e0d-9da3-58b1a7d7b432)

We now have a flag!

Thanks for reading and I hope you enjoyed it, Leave a like if you do.








  

