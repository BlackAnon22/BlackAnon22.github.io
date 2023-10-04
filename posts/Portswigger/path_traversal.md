# Lab: File path traversal, simple case
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6923998b-ef81-478c-8142-7039dca4d4d8)

Our task is to retrieve the contents of the ```/etc/passwd``` file.

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5a66c13f-89ca-45b7-90a4-d368eb5cea34)

Right-click on an image and try to open it another tab, we'll capture this request and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/98d8eb19-6bc4-4700-a3a4-b5a42a8e94b2)

Replace the ```20.jpg``` with ```../../../../../../etc/passwd```. This should read the ```/etc/passwd``` file to us

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1f93a5f8-99d1-4a52-a3e9-f32218e9c6ed)

Nice

Checking the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/38134a58-f682-4d9e-9f05-4ef408219ec8)

We have successfully solved the lab

--------------------

# Lab: File path traversal, traversal sequences blocked with absolute path bypass
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fad452dd-8b6b-4b99-be47-91076d8f289f)

Our task is to read the content of the ```/etc/passwd``` file but defenses has been implemented against path traversal attacks. So we have to bypass this to read the file

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6305bfc3-07b9-4bdd-b0f9-c306039c3895)

Right-click on an image, then click "open image in new tab", doing this we'll capture the request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/04897461-cd89-4b10-8132-d752a6ce1038)

cool, now lets replace ```23.jpg``` with the path ```../../../../../../etc/passwd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cf93b9d6-eda8-4be4-a3c0-fef19f81b8f2)

We get the "No such file" message, this is probably because of the defence mechanism that was set up

To bypass this we'll use an absolute path from the filesystem root, so we'll have the path ```/etc/passwd```. Lets try this path

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/78111726-55b5-4922-9c83-287bca015507)

Checking the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1394adba-f48e-4335-be31-014fae2be4d3)

We have successfully solved this lab

-------------------------

# Lab: File path traversal, traversal sequences stripped non-recursively
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/826bd87a-8337-42a2-887a-2c5badd9dfae)

Our task is to retrieve the ```/etc/passwd``` file

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4f0781a2-7101-46ee-ba38-c85ec6aaecd5)

Right-click on an image and try to open the image in a new tab, while we do that we'll capture the request using burpsuite and we'll send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2c53f3f3-6a8e-4f8b-a0b8-ba8a93d710e4)

Replace the ```23.jpg``` with the file path ```/etc/passwd```, lets see what happens when we do that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/31cfc10f-06d9-4455-bc53-14f3d973a812)

oops, it didn't work. This is because the application strips path traversal sequences from the user-supplied filename before using it. 

To bypass this, we use nested traversal sequences. So we can try using the file path ```....//....//....//etc/passwd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3296a330-7a23-4ce2-98ec-cad4c93e8e31)

Checking the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9b2ae0ce-2143-40a3-aa75-8625f6a0e7c1)

We have successfully completed this lab

-------------------




















