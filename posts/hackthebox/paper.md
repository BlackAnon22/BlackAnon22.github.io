# Box: Paper
# Level: Easy
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.136.31 -T4  -v -p-```

```
Nmap scan report for 10.129.136.31
Host is up (0.15s latency).
Not shown: 65532 closed tcp ports (reset)
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 8.0 (protocol 2.0)
| ssh-hostkey: 
|   2048 1005ea5056a600cb1c9c93df5f83e064 (RSA)
|   256 588c821cc6632a83875c2f2b4f4dc379 (ECDSA)
|_  256 3178afd13bc42e9d604eeb5d03eca022 (ED25519)
80/tcp  open  http     Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1k mod_fcgid/2.3.9)
|_http-generator: HTML Tidy for HTML5 for Linux version 5.7.28
|_http-title: HTTP Server Test Page powered by CentOS
| http-methods: 
|   Supported Methods: OPTIONS HEAD GET POST TRACE
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.37 (centos) OpenSSL/1.1.1k mod_fcgid/2.3.9
443/tcp open  ssl/http Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1k mod_fcgid/2.3.9)
|_http-generator: HTML Tidy for HTML5 for Linux version 5.7.28
| http-methods: 
|   Supported Methods: OPTIONS HEAD GET POST TRACE
|_  Potentially risky methods: TRACE
|_http-title: HTTP Server Test Page powered by CentOS
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=Unspecified/countryName=US
| Subject Alternative Name: DNS:localhost.localdomain
| Issuer: commonName=localhost.localdomain/organizationName=Unspecified/countryName=US
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-07-03T08:52:34
| Not valid after:  2022-07-08T10:32:34
| MD5:   579a92bd803cac47d49c5adde44e4f84
|_SHA-1: 61a2301f9e5c2603a64300b5e5da5fd5c175f3a9
| tls-alpn: 
|_  http/1.1
|_http-server-header: Apache/2.4.37 (centos) OpenSSL/1.1.1k mod_fcgid/2.3.9
|_ssl-date: TLS randomness does not represent time
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=9/14%OT=22%CT=1%CU=32191%PV=Y%DS=2%DC=T%G=Y%TM=650286C
OS:3%P=x86_64-pc-linux-gnu)SEQ(SP=104%GCD=2%ISR=10C%TI=Z%CI=Z%TS=A)SEQ(SP=1
OS:04%GCD=1%ISR=10C%TI=Z%CI=Z%II=I%TS=A)OPS(O1=M539ST11NW7%O2=M539ST11NW7%O
OS:3=M539NNT11NW7%O4=M539ST11NW7%O5=M539ST11NW7%O6=M539ST11)WIN(W1=7120%W2=
OS:7120%W3=7120%W4=7120%W5=7120%W6=7120)ECN(R=Y%DF=Y%T=40%W=7210%O=M539NNSN
OS:W7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%D
OS:F=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O
OS:=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=N)U1(R=Y%DF=N
OS:%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%C
OS:D=S)

Uptime guess: 46.864 days (since Sat Jul 29 08:22:13 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=260 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE (using port 53/tcp)
HOP RTT       ADDRESS
1   150.24 ms 10.10.14.1
2   150.10 ms 10.129.136.31

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
```

From the above scan we have 3 open ports. Port 22 which runs ssh, port 80 which runs http, port 443 which runs ssl/http. Well, our ennumeration today will be focused on the http service.



# Enumeration

Lets start by adding the IP address to our ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ sudo nano /etc/hosts
[sudo] password for bl4ck4non: 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ cat /etc/hosts 
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
10.129.136.31 paper.htb
```
Good. Now lets navigate to the webpage ```paper.htb```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/37753a5c-546a-4ad8-a793-ec52ac71cd93)

Lets fuzz for directories

command:```ffuf -u "http://paper.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ ffuf -u "http://paper.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://paper.htb/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________
cgi-bin/                [Status: 403, Size: 199, Words: 14, Lines: 8, Duration: 158ms]
manual                  [Status: 301, Size: 232, Words: 14, Lines: 8, Duration: 151ms]
:: Progress: [32298/32298] :: Job [1/1] :: 241 req/sec :: Duration: [0:02:15] :: Errors: 0 ::
```
oops, nothing interesting here

Lets view the http header for this webpage using curl

command:```curl -I http://paper.htb```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8830c574-dc95-4e31-9d16-38f8a3e2ee9a)

we found something interesting hehe, there's a backend server ```office.paper``` that is handling our requests. Lets add this to our ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ sudo nano /etc/hosts
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ cat /etc/hosts 
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
10.129.136.31 paper.htb office.paper
```
Cool, now we can navigate to the wepage ```office.paper```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/65263496-d6ec-4cc9-a0ea-b06e1c6127cb)

Alright so this is a wordpress site, ```wordpress 5.2.3``` to be exact.



# Exploitation

This wordpress version has an available exploit. It is vulnerable to ```CVE-2019-17671```. You can access the exploit [here](https://www.exploit-db.com/exploits/47690)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3d62b35d-049f-45bc-a60a-5bff41a21c05)

Adding ```?static=1``` to the back of the url

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80b8cbd5-e3d7-46f1-bcde-9e0f6f54b1fc)

So that was an unpublished draft we just viewed. As we can see there's a secret registration url for new employees chat system, this is being hosted on a subdomain, so we'll be adding ```chat.office.paper``` to our ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ sudo nano /etc/hosts        
[sudo] password for bl4ck4non: 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
10.129.136.31 paper.htb office.paper chat.office.paper
```
Lets navigate to the registration page ```http://chat.office.paper/register/8qozr226AhkCHZdyY```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2d067ce2-eaa5-400e-80da-d48e37b345fa)

Registering a new account,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6e20f7f5-5d84-4ddb-be38-8ac7065b2a60)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b0c3788d-1d04-4099-98d4-c5b8fa31b18a)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e363dbda-582c-4988-aa02-bfe97fb8f9b0)

Click on "general",

This conversation box is "view only" but we can see there's a bot on the group chat

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e663411a-f68f-47f2-b172-7c323d67e19a)

So, there's a bot that handles the chat group

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ebd31551-c05f-40c8-9657-96f6d48ea13d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b0a45919-c30d-47c4-9fb5-157848b076e7)

So, the bot can help list files. But how do we access this bot??

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0484ed81-0e43-456d-9f34-574f13241ca4)

Well, lets send the bot a dm hehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c38f7878-e6dd-4dd4-b135-ab26747bceca)

From the above screenshot, you can see I used the ```list``` command, and the bot listed the files under the ```/sales``` directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/34765399-3b8b-4953-a868-ad02218b8e03)

I took it up a notch by trying to view a directory in the ```/sales``` directory using the command ```list sales```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2afa91b2-bb54-4fda-94b5-92a3dc1ea2a9)

Cool, we can use the ```file``` command to read files. We can try this for the ```/etc/passwd``` file too I think🤔

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/64531f4c-3c3d-4bd9-8277-2a991cd927af)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/68b20f80-e251-4936-a5a9-2a4e61c98fbd)

It worked hehe😎

Well, I found an intersting file in user ```Dwight``` home directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bd8e65d0-992a-4bbb-9f26-ef7456c13e38)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/724ca109-222f-4a2d-94aa-9d7f4b9b85b5)

Reading the file,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/96dce1e6-a102-45fc-9931-4fb2c72d49ef)

We found a password hehe😄

Well that password  works well for user ```dwight```😂

What we can do now is ssh into the server as user ```dwight```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9ab83300-fd39-4723-8b84-bcb282424cc2)

We are in hehe. Lets go ahead and escalate our privileges



# Privilege Escalation



















