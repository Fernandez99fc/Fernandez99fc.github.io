# Where are the robots?
* Type: Web Exploitation
* Link: https://play.picoctf.org/challenge/4

  ![Screenshot (601)](https://github.com/Fernandez99fc/cybersec/assets/172477285/2fc4a8e5-2213-42b8-9888-1e992fa7536f)

We have been provided a link above to visit. We get a blank page with the message below
![Screenshot (602)](https://github.com/Fernandez99fc/cybersec/assets/172477285/9b2af35f-f236-45b5-a144-99c8ed61c95f)

The hint button on the page could tell us that the admin doesn't want us to see some parts of the website. This is mostly specified in the robots.txt file to tell web crawlers which area of the website should be shown to normal users.
An attacker can try to  visit the file by placing the file path at the end of the url

![Screenshot (5)](https://github.com/Fernandez99fc/cybersec/assets/172477285/71264cae-211e-4afe-aef4-1d270e98c186)
When we visit the robots.txt file. We can see we've been restricted access access to /477ce.html file. Let's try to view the content of the file.
![Screenshot (6)](https://github.com/Fernandez99fc/cybersec/assets/172477285/cf22a42c-2a74-4bda-a658-eeed5797efc9)
Here we go, we got the root flag!

