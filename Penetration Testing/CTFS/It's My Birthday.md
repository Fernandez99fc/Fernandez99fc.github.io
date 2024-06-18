* Link: https://play.picoctf.org/practice/challenge/109
* Challenge:** WEB EXPLOITATION

![Screenshot (7)](https://github.com/Fernandez99fc/cybersec/assets/172477285/21762913-9f77-43d8-90da-986437adf766)

**DESCRIPTION**

I sent out 2 invitations to all of my friends for my birthday! I'll know if they get stolen because the two invites look similar, and they even have the same md5 hash, but they are slightly different! You wouldn't believe how long it took me to find a collision. Anyway, see if you're invited by submitting 2 PDFs to my website. http://mercury.picoctf.net:50970/

# Step 1
Visit the Link
![Screenshot (8)](https://github.com/Fernandez99fc/cybersec/assets/172477285/ac083783-f657-4326-a54a-b67b14c462ee)


# Goal
We are asked to submit two files to the website but in a pdf format. I've tried submitting two different pdf files but didn't work. 
The type of files we are asked to submit are files with the same Md5 checkum/hash. 

# Note:
An object is subjected to have a unique hash, Two files can't have the same hash, be it sha256,sha1,sha512,bcrypt e.t.c. If two files have the same hash value, therefore, there's a collision. In this case, there's a Md5 collision.

I came across this page: https://www.mscs.dal.ca/~selinger/md5collision/.
![Screenshot (610)](https://github.com/Fernandez99fc/cybersec/assets/172477285/dee4d122-75eb-4e9a-a9e1-21352d0a649e)

You can read more about md5 collision. I was able to find two different softwares having the same md5 hash due to collision. I dowloaded the files and added a .pdf extension to them since it is the accepted file format.

![Screenshot (609)](https://github.com/Fernandez99fc/cybersec/assets/172477285/826ec96d-b3b0-4473-b437-b07c9ae002cc)
After renaming, clicl submit and we should have a flag at the bottom of the page source code.
![Screenshot (608)](https://github.com/Fernandez99fc/cybersec/assets/172477285/337a8804-5671-4ed0-8fcf-c59c36ff1fff)






