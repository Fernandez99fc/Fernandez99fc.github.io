# Defend The Web Task 3
 * Link: https://defendtheweb.net/playground/where-am-i?getoutofhere
* Type: WEB APPLICATION EXPLOITATION

  ![Screenshot (9)](https://github.com/Fernandez99fc/cybersec/assets/172477285/14bcf64b-ac92-47c2-835f-1e4a91ed0102)
te
Found nothing after inspecting the page source code. The next thing is to capture how the request flows to the server using burpsuite.
I will open burpsuite and turn on interception. Reload the page and we should be able to capture the traffic.
![VirtualBox_LINUX SERVER_24_04_2024_08_20_26](https://github.com/Fernandez99fc/cybersec/assets/172477285/5568d2cd-2793-499d-832d-e095fa7a3f94)

The page has a password login field, we can enter a random password and capture the request again using burpsuite to understand the flow.
![VirtualBox_LINUX SERVER_24_04_2024_08_28_05](https://github.com/Fernandez99fc/cybersec/assets/172477285/c928ca1e-bea0-45c2-87f9-a3dc9e8ca62d)

There's nothing interesting to do after that. We still don't know what the password is. We cam take a look at the string "getoutofhere" at the end of the post request. We can perform string manipulation by changing the string to something else, then forward to repeater and see the response we get from the server.
![VirtualBox_LINUX SERVER_24_04_2024_08_28_05](https://github.com/Fernandez99fc/cybersec/assets/172477285/59ddfa12-e7db-4ad6-9a33-497561e3eeac)

How do we know what string to change to? Using reverse psychology, we can think of "getinhere" as "login" and "getoutofhere" as logout/signout. Same meaning different strings right?
Since we want to login, we change "getoutofhere" to "login". We can forward the request first to the reapter, then change the string and forward to the server to see what response we get.

![VirtualBox_LINUX SERVER_24_04_2024_08_32_34](https://github.com/Fernandez99fc/cybersec/assets/172477285/78050e03-58d2-4da7-a61d-1742a2c5b456)

On the response page, we could see the password, then we can use it to login in the login page.

Goodluck!


