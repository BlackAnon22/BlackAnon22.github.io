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

# Lab: File path traversal, traversal sequences stripped with superfluous URL-decode
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/06c243a5-8a46-449e-bf07-9714a955b0fe)

Our task is to read the content of the file ```/etc/passwd```

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0e520dbd-b5e6-41ab-a5d2-89af3bb6817d)

Right-click on the image to open in a new tab, while we do this we'll capture the request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c90a3eb2-0785-4b73-afe3-da9d36af6fd9)

Lets replace ```34.jpg``` to the file path ```../../../etc/passwd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4e89d083-2e89-41e7-b8f8-d12cc5d1c442)

We get the "No such file" message. Well, this is because the application blocks input containing path traversal sequences. It then performs a URL-decode of the input before using it. 

So, what we can do is url encoding our file path, so we can use the file path ```..%252f..%252f..%252fetc/passwd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80ba952d-6ec0-4d46-af1d-77fc0c075453)

Checking the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/09477c01-83c9-4b1b-af48-a123d9573275)

We have successfully solved this lab

------------------------

# Lab: File path traversal, validation of start of path
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9656e116-17c2-442e-996e-521f388a6649)

Our task is to view the content of the ```/etc/passwd``` file

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cbcc41c4-005a-4a0a-9e5b-4db5b25a6af1)

Right-click on an image, then open it in a new tab. We'll capture that request and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6ebe2518-6ea3-4d86-bfba-60732e44eab6)

cool, now application transmits the full file path via a request parameter, and validates that the supplied path starts with the expected folder. So to solve this we'll include the required base folder followed by suitable traversal sequences

This means we'll have something like this ```/var/www/images/../../../etc/passwd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/860ed637-b467-4547-87fc-64e2bad8d6b7)

Nice, we got the content of the ```/etc/passwd``` file

Checking the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f362e083-1345-4832-9f06-bd7a9ab5e6fe)

We have successfully solved this lab

-----------------

# Lab: File path traversal, validation of file extension with null byte bypass
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/503b4ca8-fd64-44c4-81b7-efdd63b2bbd4)

Our task is to read the ```/etc/passwd``` file

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/af46b765-3a12-446f-b6fc-41d63926efe2)

Right-click on an image, click on "open image in a new tab", we'll capture the request using burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/523dd8ea-669e-4daa-acad-a822938eb365)

We know that the application validates that the supplied filename ends with the expected file extension, what we can do is try to use a null byte to effectively terminate the file path before the required extension.

<font color="Green">A null byte, often represented as '\0' in programming, is a character with a value of zero. It is used to terminate strings in C-style languages and can also be used in various contexts to denote the end of data or a delimiter.
</font>

So, we'll have a file path like this ```../../../etc/passwd%00.jpg```.

Lets replace ```15.jpg``` with that file path

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3d6b8442-6da2-455d-b99a-8c7b99af5b61)

cool stuff, we are able to read the content of the ```/etc/passwd``` file

Checking the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/75197a75-c29d-45bd-9fd8-edad7b10d5cf)

We have successfully solved this labs.

This marks the end of the Path Traversal labs😎
<br><br>
[Back To Home](../../index.md)













