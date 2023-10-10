# Box Name: Heist
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.96.157 -p- -v -T4```

```
Nmap scan report for 10.129.96.157
Host is up (0.40s latency).
Not shown: 65530 filtered tcp ports (no-response)
PORT      STATE SERVICE       VERSION
80/tcp    open  http          Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| http-title: Support Login Page
|_Requested resource was login.php
135/tcp   open  msrpc         Microsoft Windows RPC
445/tcp   open  microsoft-ds?
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
49669/tcp open  unknown
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
OS fingerprint not ideal because: Missing a closed TCP port so results incomplete
No OS matches for host
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=264 (Good luck!)
IP ID Sequence Generation: Randomized
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-10-10T19:48:09
|_  start_date: N/A
|_clock-skew: -1s

TRACEROUTE (using port 445/tcp)
HOP RTT       ADDRESS
1   339.57 ms 10.10.16.1
2   340.07 ms 10.129.96.157

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Tue Oct 10 20:48:49 2023 -- 1 IP address (1 host up) scanned in 436.02 seconds
```
From our nmap scan we have quite a number of ports opened. We'll start our enumeration today from port 80



# Enumeration (Port 80)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2bc80794-25ca-4678-a4fb-5ca4fb869bb6)

We get this login page. Since we don't have any creds lets login as guest

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58e61a19-7993-42ce-bdbf-8c6d4c00e149)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d10915da-73c3-4987-bd9a-f3993ec38178)

Nice, this is a conversation between user ```Hazard``` and the ```admin```. 

Lets check out the configuration file user ```Hazard``` sent.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ce07dae4-06f7-4a39-96f6-d0f0e693bc2f)

From the above screenshot we can see encrypted passwords for users ```Hazard```, ```rout3r``` and ```admin```.

Lets try to crack the first password

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/heist]
└─$ nano hash                                                        
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/heist]
└─$ john hash --wordlist=/usr/share/wordlists/rockyou.txt            
Warning: detected hash type "md5crypt", but the string is also recognized as "md5crypt-long"
Use the "--format=md5crypt-long" option to force loading these as that type instead
Using default input encoding: UTF-8
Loaded 1 password hash (md5crypt, crypt(3) $1$ (and variants) [MD5 256/256 AVX2 8x3])
Will run 8 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
stealth1agent    (?)     
1g 0:00:01:07 DONE (2023-10-10 21:09) 0.01479g/s 51878p/s 51878c/s 51878C/s stealthy001..stcroix85
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/heist]
└─$ cat hash
$1$pdQG$o8nrSzsGXeaduXrjlvKc91
```
We got the password to be ```stealth1agent```. Lets try gain access using winrm

command:```evil-winrm -u hazard -i 10.129.96.157 -p 'stealth1agent' -S```




























