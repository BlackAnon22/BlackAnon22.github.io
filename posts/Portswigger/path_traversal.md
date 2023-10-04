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
