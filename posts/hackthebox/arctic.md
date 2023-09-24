# Box: Arctic
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A -T4 -v -p-  10.129.108.187```

```
Nmap scan report for 10.129.108.187
Host is up (0.19s latency).
Not shown: 65532 filtered tcp ports (no-response)
PORT      STATE SERVICE VERSION
135/tcp   open  msrpc   Microsoft Windows RPC
8500/tcp  open  http    JRun Web Server
|_http-title: Index of /
49154/tcp open  msrpc   Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose|phone|specialized
Running (JUST GUESSING): Microsoft Windows 8|Phone|2008|7|8.1|Vista|2012 (92%)
OS CPE: cpe:/o:microsoft:windows_8 cpe:/o:microsoft:windows cpe:/o:microsoft:windows_server_2008:r2 cpe:/o:microsoft:windows_7 cpe:/o:microsoft:windows_8.1 cpe:/o:microsoft:windows_vista::- cpe:/o:microsoft:windows_vista::sp1 cpe:/o:microsoft:windows_server_2012
Aggressive OS guesses: Microsoft Windows 8.1 Update 1 (92%), Microsoft Windows Phone 7.5 or 8.0 (92%), Microsoft Windows 7 or Windows Server 2008 R2 (91%), Microsoft Windows Server 2008 R2 (91%), Microsoft Windows Server 2008 R2 or Windows 8.1 (91%), Microsoft Windows Server 2008 R2 SP1 or Windows 8 (91%), Microsoft Windows 7 (91%), Microsoft Windows 7 Professional or Windows 8 (91%), Microsoft Windows 7 SP1 or Windows Server 2008 R2 (91%), Microsoft Windows 7 SP1 or Windows Server 2008 SP2 or 2008 R2 SP1 (91%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.007 days (since Fri Sep 22 00:28:52 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE (using port 135/tcp)
HOP RTT       ADDRESS
1   222.51 ms 10.10.14.1
2   222.63 ms 10.129.108.187

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Sep 22 00:39:11 2023 -- 1 IP address (1 host up) scanned in 379.45 seconds
```
From our scan we have 3 open ports, we have a port 8500 that runs the http service. Our enumeration today will be focused on that port.



# Enumeration (Port 8500)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/005c79fd-6322-4e10-b7f5-a42210cd5721)

Checking the directories, I found this login page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c142b585-6539-46a6-a06d-4b0388083778)

From the above screenshot we can see that ```Adobe ColdFusion``` is being used on this webpage

Lets try using default passwords for the login page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/336d2dab-2ba4-4afd-96ab-a08cd9404add)

oops, doesn't work🥲

Well, I found an exploit for this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dac6ffd1-8704-45a4-8091-9f766a84137a)

So, it is vulnerabale to ```CVE-2010-2861```. You can get it [here](https://www.exploit-db.com/exploits/14641) 

Reading the exploit, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7f0ea944-f3f0-4d95-90d6-999e9bd2b7b8)

This means we can exploit this webpage using directory transversal. Well, this is not a Linux box, I would have said we should try reading the ```/etc/passwd``` file😂. 

After a little research, I found out that ColdFusion 8 passwords are typically stored in an encrypted format in a configuration file called ```password.properties```. This file is used to store various ColdFusion passwords, including the administrator password and datasources passwords. The full path is typically ```[ColdFusion Installation Directory]/lib/password.properties```.

So we'll try to read the ```password.properties``` by navigating to the url ```?locale=../../../../../../../../../../ColdFusion8/lib/password.properties%00en```


















