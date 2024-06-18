# CTFLEARN CHALLENGE 114

* Link: https://ctflearn/challenge/114
  
* Difficulty: Medium

* Objective: The website requires authentication via POST request only. 

![VirtualBox_LINUX SERVER_17_04_2024_13_16_26](https://github.com/Fernandez99fc/cybersec/assets/172477285/1feb1f6b-e168-4740-9f68-82d3f8fcf689)

Visiting the website displays a message indicating that we haven't submitted POST data that the website requires for authentication.
![VirtualBox_LINUX SERVER_17_04_2024_13_24_04](https://github.com/Fernandez99fc/cybersec/assets/172477285/090fd751-347e-4c67-b2f0-cf3242b6e8a2)

The first thing we can do is reading the page source of the page if we can see exposed credentials. Sometimes, admin credentials are being left exposed in the page source. We can do this by right-clicking the page and click on view page source. We can read through or search for strings such as "user","pass","hidden".
![VirtualBox_LINUX SERVER_17_04_2024_13_28_22](https://github.com/Fernandez99fc/cybersec/assets/172477285/800fecd7-f4c9-4b5d-b885-b377e9036d52)

We could find a user account and a password. Since the website only accepts a POST request and we don't have a GUI(graphical user Interface) to login, We can use 'CURL' which is a command line tool used for managing http requests. It can be used to download data(e.g files), post data and manage other http requests.

![VirtualBox_LINUX SERVER_17_04_2024_13_59_53](https://github.com/Fernandez99fc/cybersec/assets/172477285/db9dcb96-eb3f-40ae-b881-f20e9a991d64)

By using the syntax "curl -X POST http://165.227.106.113/post.php -d "key=value"

* -X - To specify the http method which is "POST"
  
* http://165.227.106.113/post.php - The url we are submitting the post request to.
  
* -d - To specify the post data to be sent.

  Flag= flag{p0st_d4t4_4ll_d4y}
  
